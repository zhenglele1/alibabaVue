<template>
  <div>
    componetPage
    <button @click="func">a</button>
    <button>a</button>
    <component :is="cut"></component>
  </div>
</template>

<script>
import a from "./a.vue";
import b from "./b.vue";
export default {
  name: "componetPage",
  props: {
    msg: String,
  },
  data() {
    return {
      cut: b,
    };
  },
  methods: {
    func() {
      if (this.cut == a) {
        this.cut = b;
      }
      this.cut = a;
    },
  },
};
</script>
