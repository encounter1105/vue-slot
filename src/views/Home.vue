// 父组件 默认插槽
<!--<template>-->
  <!--<div class="container">-->
    <!--&lt;!&ndash; 默认插槽&ndash;&gt;-->
    <!--<child>-->
      <!--<template>内容</template>-->
      <!--&lt;!&ndash; <template v-slot:default>但如果你定义了 default 之后，其他内容就不会出现了，原理同上，不能重复定义</template> &ndash;&gt;-->
    <!--</child>-->

    <!--&lt;!&ndash; 独占默认插槽的缩写 &ndash;&gt;-->
    <!--<child v-slot="slotProps">-->
      <!--当只有默认插槽时，此为独占默认插槽的缩写<br>-->
      <!--如果组件中有其他具名插槽，这么写会报错<br>-->
      <!--slotProps 取的是，子组件标签 slot 上属性数据的集合-->
    <!--</child>-->
  <!--</div>-->
<!--</template>-->

// 父组件 具名插槽
<!--<template>-->
  <!--<div class="container">-->
    <!--&lt;!&ndash; 具名插槽使用 &ndash;&gt;-->
    <!--<child>-->
      <!--<template v-slot:main>-->
        <!--<a href="https://www.zcygov.cn" target="_blank">导航</a>-->
      <!--</template>-->
      <!--<template #footer>页脚（具名插槽的缩写#）</template>-->
      <!--<template #footer>-->
        <!--&lt;!&ndash;  v-slot 重复定义同样的 name 后只会加载最后一个定义的插槽内容 &ndash;&gt;-->
        <!--v-slot只会添加在一个 template 上面-->
      <!--</template>-->
    <!--</child>-->
  <!--</div>-->
<!--</template>-->

// 父组件 作用域插槽
<template>
  <div class="container">
    <!-- 作用域插槽，以及解构插槽 Prop 的写法 -->
    <child>
      <template #footer="slotProps">
        {{slotProps.user.title}}
        <button @click="slotProps.testClick">点我</button>
      </template>
      <template #footer="{user,testClick}">
        {{user.title}}<br>
        此为解构插槽prop<br>
        <!-- 子组件中的通用方法，可传递给父组件复用 -->
        <button @click="testClick">点我</button>
      </template>
    </child>
  </div>
</template>

<script>
// @ is an alias to /src
import child from './child.vue'

export default {
  name: 'Home',
  components: {
    child
  }
}
</script>
