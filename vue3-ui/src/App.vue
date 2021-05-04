<template>
  <div>
    <!-- <img alt="Vue logo" src="./assets/logo.png" /> -->
    <button @click="Vshow()">hellow组件</button
    ><button @click="Vshow()">生命周期组件</button>
    <!-- <HelloWorld msg="Hello Vue 3.0 + Vite" /> -->
    <component :is="cut"></component>
    <component :is="show"></component>
  </div>
</template>

<script>
import HelloWorld from "./components/HelloWorld.vue";
import componetPage from "./components/componetPage.vue";
import { onMounted, onBeforeMount, onBeforeUpdate } from "vue";
import { onBeforeUnmount, onUnmounted, onUpdated } from "@vue/runtime-core";
export default {
  name: "App",
  // components: {
  //   HelloWorld,
  //   componetPage,
  // },
  beforeCreate() {
    console.log("beforeCreate: ");
  },
  created() {
    console.log("created: ");
  },
  beforeMount() {
    console.log("beforeMount: ");
  },
  mounted() {
    console.log("mounted: ");
  },
  beforeUpdate() {
    console.log("beforeUpdate: ");
  },
  updated() {
    console.log("updated: ");
  },
  beforeUnmount() {
    console.log("beforeUnmount: ");
  },
  unmounted() {
    console.log("unmounted: ");
  },
  setup() {
    console.log("setup: ");
    onBeforeMount(() => {
      console.log("onBeforeMount: ");
    });
    onBeforeUpdate(() => {
      console.log("onBeforeUpdate: ");
    });
    onUpdated(() => {
      console.log("onUpdated: ");
    });
    onBeforeUnmount(() => {
      console.log("onBeforeUnmount: ");
    });
    onUnmounted(() => {
      console.log("onUnmounted");
    });
    onMounted(() => {
      console.log("mounted completed!");
    });
    return {
      show: componetPage,
      cut: HelloWorld,
    };
  },
  methods: {
    Vshow() {
      this.cut = componetPage;
    },
  },
};
</script>
