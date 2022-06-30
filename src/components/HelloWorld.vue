<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <h2>
      这是一个供您记录任务并打卡的小小备忘录网站(*^▽^*)<br>
      <!-- Vue官方文档
      <a href="https://cli.vuejs.org" target="_blank" rel="noopener">vue-cli documentation</a>. -->
    </h2>
    <h3>常用网站链接</h3>
    <ul>
      <li><a href="https://home.code-nav.cn/" target="_blank" rel="noopener">百度</a></li>
      <li><a href="https://www.bilibili.com/" target="_blank" rel="noopener">B站</a></li>
      <li><a href="https://www.code-nav.cn/" target="_blank" rel="noopener">编程导航</a></li>
      <li><a href="https://www.csdn.net/" target="_blank" rel="noopener">CSDN</a></li>
      <li><a href="https://github.com/" target="_blank" rel="noopener">github</a></li>
    </ul>
     <h3>学校相关链接</h3>
    <ul>
      <li><a href="https://www.lnkjzm.cn/" target="_blank" rel="noopener">筑梦辽科</a></li>
      <li><a href="http://cxcyxy.lnist.edu.cn/" target="_blank" rel="noopener">创新创业学院</a></li>
      <li><a href="https://lkyjw.lnist.edu.cn/" target="_blank" rel="noopener">教务在线</a></li>
      <li><a href="http://210.30.224.150/cxxf/" target="_blank" rel="noopener">双创学分系统</a></li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: skyblue;
}
</style>
