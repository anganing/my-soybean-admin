<script setup lang="ts">
import { TresCanvas } from '@tresjs/core';
import { OrbitControls } from '@tresjs/cientos';
</script>

<template>
  <!--
  所有依赖于场景的组件必须存在于 <TresCanvas />组件内。否则，他们不会被渲染。作用：
  1、创建一个 WebGLRenderer 用于自动更新每一帧。
  2、根据浏览器刷新率设置要在每一帧上调用的渲染循环。
  默认的情况下，TresCanvas 组件会跟随父元素的宽高，如果出现空白页，请确保父元素的大小合适。
  如果场景不是用户界面的一部分，您也可以通过像这样的使用 window-size prop 来强制画布使用整个窗口的宽度和高度:
  <TresCanvas window-size>
  </TresCanvas>
   -->
  <TresCanvas clear-color="#82DBC5">
    <!--
    透视摄像机。
    相机默认位置是场景的原点（0,0,0），如果 prop position 为空， TresJS 会自动将相机的位置设置为 [3,3,3]。
    如果场景中未定义摄像机，则会自动添加透视摄像机。
    -->
    <TresPerspectiveCamera :position="[3, 3, 3]" :look-at="[0, 0, 0]" />
    <!-- 控制器，可以控制3D对象。 TresOrbitControls 组件在组件树内需要处于相机之后。这是因为控制器需要知道相机才能工作。 -->
    <OrbitControls />
    <!--
    请注意，我们不需要导入任何东西，这是因为 TresJS 会为您使用的 CamelCase 的带有 Tres 前缀的 Three 对象自动生成一个 Vue 组件。
    例如，如果要使用 <TresAmbientLight /> 组件。
    -->
    <!-- 网格 -->
    <TresMesh>
      <!-- 环面几何  -->
      <TresTorusGeometry :args="[1, 0.5, 16, 32]" />
      <!-- 材质 -->
      <TresMeshBasicMaterial color="orange" />
    </TresMesh>
    <!-- 环境光 -->
    <TresAmbientLight :intensity="1" />
  </TresCanvas>
</template>
