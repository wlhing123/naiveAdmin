<template>
  <n-menu
    :inverted="true"
    :collapsed-width="64"
    :collapsed-icon-size="22"
    :options="menuOptions"
    :value="actived"
    :collapsed="collapsed"
    @update:value="handleUpdateValue"
    class="side-menu"
  />
</template>

<style lang="less">

</style>

<script setup>
import { h, ref,inject } from 'vue';
import { Home, HomeOutline, Menu } from '@vicons/ionicons5';
import { NMenu, NIcon } from 'naive-ui';
import {Dev, User,UserEdit, ChartBar,Wpforms, Edit,Upload} from '@vicons/fa'
import {MdSettings} from '@vicons/ionicons4'
import router, {routes} from '../../router';
function renderIcon(icon) {
  return () => h(NIcon, null, { default: () => h(icon) });
}
const menuOptions=[
    {
      label:'后台管理系统',
      key:'title',
      path:'/',
    },
    {
        label:'首页',
        path:'/',
        key:'home',
        icon:renderIcon(Home)
    },
    {
      label:'echart组件',
      path:'/echart',
      key:'echart',
      icon:renderIcon(ChartBar),
      children:[
        {
          label:'折线图',
          path:'/echart/line',
          key:'line',
          icon:renderIcon(ChartBar),
        },
        {
          label:'柱状图',
          path:'/echart/bar',
          key:'bar',
          icon:renderIcon(ChartBar),
        },
        {
          label:'饼图',
          path:'/echart/pie',
          key:'pie',
          icon:renderIcon(ChartBar),
        },
        {
          label:'雷达图',
          path:'/echart/radar',
          key:'radar',
          icon:renderIcon(ChartBar),
        },
        {
          label:'环形图',
          path:'/echart/ring',
          key:'ring',
          icon:renderIcon(ChartBar),
        }

      ]
    },
    {
      label:'表单组件',
      path:'/form',
      key:'form',
      icon:renderIcon(Wpforms),
      children:[
        {
          label:'富文本编辑器',
          path:'/form/editor',
          key:'editor',
          icon:renderIcon(Edit),
        },
        {
          label:'上传组件',
          path:'/form/upload',
          key:'upload',
          icon:renderIcon(Upload),
        }
      ]
    },
    {
      label:'系统管理',
      path:'/sys',
      key:'system',
      icon:renderIcon(MdSettings),
      children:[
        {
          label:'用户管理',
          path:'/sys/user',
          key:'user',
          icon:renderIcon(User)
        },
        {
          label:'角色管理',
          path:'/sys/role',
          key:'role',
          icon:renderIcon(UserEdit)
        },
        
      ]
    },
    
]

let actived=ref('')
function handleUpdateValue(key,item){
  actived.value=key
  router.push(item.path)
}



</script>


