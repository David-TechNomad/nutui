<template>
  <Demo>
    <h2>基础使用</h2>
    <nut-config-provider :theme="theme">
      <nut-cell title="切换暗黑">
        <template #link>
          <nut-switch v-model="switchChecked" @change="switchChange" />
        </template>
      </nut-cell>
      <nut-cell title="我是标题" sub-title="副标题描述" desc="描述文字"></nut-cell>

      <nut-form>
        <nut-form-item label="开关">
          <nut-switch v-model="formData2.switch"></nut-switch>
        </nut-form-item>
        <nut-form-item label="复选框">
          <nut-checkbox v-model="formData2.checkbox">复选框</nut-checkbox>
        </nut-form-item>
        <nut-form-item label="单选按钮">
          <nut-radio-group v-model="formData2.radio" direction="horizontal">
            <nut-radio label="1">选项1</nut-radio>
            <nut-radio disabled label="2">选项2</nut-radio>
            <nut-radio label="3">选项3</nut-radio>
          </nut-radio-group>
        </nut-form-item>
        <nut-form-item label="评分">
          <nut-rate v-model="formData2.rate" />
        </nut-form-item>
        <nut-form-item label="步进器">
          <nut-input-number v-model="formData2.number" />
        </nut-form-item>
        <nut-form-item label="滑块">
          <nut-range v-model="formData2.range" hidden-tag></nut-range>
        </nut-form-item>
        <nut-form-item label="文件上传">
          <nut-uploader v-model:file-list="formData2.defaultFileList" url="http://服务地址" maximum="3" multiple>
          </nut-uploader>
        </nut-form-item>
        <nut-form-item label="地址">
          <input
            v-model="formData2.address"
            class="nut-input-text"
            readonly
            placeholder="请选择地址"
            type="text"
            @click="addressModule.methods.show"
          />
          <!-- nut-address -->
          <nut-address
            v-model:visible="addressModule.state.show"
            :province="addressModule.state.province"
            :city="addressModule.state.city"
            :country="addressModule.state.country"
            :town="addressModule.state.town"
            custom-address-title="请选择所在地区"
            @close="addressModule.methods.onClose"
          ></nut-address>
        </nut-form-item>
      </nut-form>
    </nut-config-provider>
    <h2>动态主题</h2>
    <nut-config-provider :theme-vars="themeVars">
      <nut-form>
        <nut-form-item label="滑块">
          <nut-range v-model="formData2.range" hidden-tag></nut-range>
        </nut-form-item>
      </nut-form>
    </nut-config-provider>
  </Demo>
</template>
<script setup lang="ts">
import { reactive, ref } from 'vue';
const switchChecked = ref(false);
const theme = ref('');
const switchChange = (v: boolean) => {
  theme.value = v ? 'dark' : '';
};
const formData2 = reactive({
  switch: false,
  checkbox: false,
  radio: 0,
  number: 0,
  rate: 3,
  range: 30,
  address: '',
  defaultFileList: [
    {
      name: 'file 1.png',
      url: 'https://m.360buyimg.com/babel/jfs/t1/164410/22/25162/93384/616eac6cE6c711350/0cac53c1b82e1b05.gif',
      status: 'success',
      message: '上传成功',
      type: 'image'
    },
    {
      name: 'file 2.png',
      url: 'https://m.360buyimg.com/babel/jfs/t1/164410/22/25162/93384/616eac6cE6c711350/0cac53c1b82e1b05.gif',
      status: 'uploading',
      message: '上传中...',
      type: 'image'
    }
  ]
});

const addressModule = reactive({
  state: {
    show: false,
    province: [
      { id: 1, name: '北京' },
      { id: 2, name: '广西' },
      { id: 3, name: '江西' },
      { id: 4, name: '四川' }
    ],
    city: [
      { id: 7, name: '朝阳区' },
      { id: 8, name: '崇文区' },
      { id: 9, name: '昌平区' },
      { id: 6, name: '石景山区' }
    ],
    country: [
      { id: 3, name: '八里庄街道' },
      { id: 9, name: '北苑' },
      { id: 4, name: '常营乡' }
    ],
    town: []
  },
  methods: {
    show() {
      addressModule.state.show = !addressModule.state.show;
      if (addressModule.state.show) {
        formData2.address = '';
      }
    },
    onClose({ data }: any) {
      formData2.address = data.addressStr;
      addressModule.state.show = false;
    }
  }
});
let color = reactive({
  primaryColor: '#008000',
  primaryColorEnd: '#008000'
});
const themeVars = color;
</script>
