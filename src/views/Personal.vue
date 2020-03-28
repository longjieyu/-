<template>
  <div class="container">
    <!-- 顶部的导航条 -->
    <div class="navigate-bar">
      <!-- $router.back()是实例下的属性，可以直接在模板中渲染 -->
      <span class="iconfont iconjiantou2" @click="$router.back()"></span>
      <strong>个人中心</strong>
      <!-- $router.push()是实例下的属性，可以直接在模板中渲染 -->
      <span class="iconfont iconshouye" @click="$router.push('/')"></span>
    </div>

    <!-- 头部 -->
    <div class="header">
      <!-- 头像 -->
      <div class="avatar">
        <!-- $axios.defaults.baseURL 就是后台的基准路径 -->
        <img :src="$axios.defaults.baseURL + userInfo.head_img" />
      </div>
      <!-- 姓名 -->
      <div class="profile">
        <div>
          <!-- 性别男的图标 -->
          <span class="iconfont iconxingbienan" v-if="userInfo.gender === 1"></span>
          <!-- 性别女的图标 -->
          <span class="iconfont iconxingbienv" v-if="userInfo.gender === 0"></span>
          {{userInfo.nickname}}
        </div>
        <p>{{moment(userInfo.create_data).format('YYYY-MM-DD')}}</p>
      </div>
      <!-- 右侧的箭头图标 -->
      <span class="arrow iconfont iconjiantou1"></span>
    </div>

    <!-- 组件的调用，单双标签都可以 -->
    <!-- :key不是报错，可以不加，
    但是vue希望给循环的元素指定“唯一的key”，所以推荐我们在循环时候都加上-->
    <Listbar v-for="(item,index) in rows" :key="index" :label="item.label" :tips="item.tips" />

    <!-- handleClick点击退出按钮时候触发 -->
    <!-- click.native这个事件类型，会给Listbar这个组件最外部的div强制绑定点击事件
    不要去跟事件传递作比较-->
    <Listbar @click.native="handleClick" label="退出" />
  </div>
</template>


<script>
// 导入列表按钮栏的组件，import后面接上的组件变量名（变量就意味着可以随便改名字）
// @代表src目录

export default {

};
</script>