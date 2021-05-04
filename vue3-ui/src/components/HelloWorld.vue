<template>
  <div>
    <h1>{{ msg }}</h1>
    <input type="text" v-model="inputValue" /><button @click="addList">
      添加
    </button>
    <ul>
      <li v-for="(item, index) in list" :key="index">
        <span v-if="item.inp">{{ item.name }}</span>
        <input
          ref="btn"
          v-else
          type="text"
          v-model="item.name"
          @blur="blur(index)"
        />
        <input type="file" />
        <button @click="oneUpload">一键上传</button>
        <button @click="edit(index)">编辑</button>
        <button @click="del(index)">删除</button>
        <button @click="success(index)">
          {{ item.state == 1 ? "完成" : "未完成" }}
        </button>
      </li>
    </ul>
    <button
      @click="
        {
          count++;
          a();
        }
      "
    >
      count is: {{ count }}
    </button>
    <button
      @click="
        {
          a();
          count--;
        }
      "
    >
      count is: {{ count }}
    </button>
    <button @click="gitImgCode">调接口</button>
    <button @click="oneExport">一键导出</button>
    <div v-html="dataImage" @click="gitImgCode"></div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "HelloWorld",
  props: {
    msg: String,
  },
  data() {
    return {
      inputValue: "",
      dataImage: "",
      count: 0,
      list: [
        { name: "llll", state: 1, inp: true },
        { name: "eee", state: 2, inp: true },
        { name: "ggeg", state: 1, inp: true },
        { name: "egege", state: 8, inp: true },
      ],
    };
  },
  methods: {
    a() {
      console.log("aaa");
    },
    edit(index) {
      setTimeout(() => {
        this.$refs.btn.focus();
      });
      this.list[index].inp = false;
    },
    blur(index) {
      console.log(this.list);
      this.list[index].inp = true;
    },
    del(index) {
      this.list.splice(index, 1);
    },
    addList() {
      this.list.push({ name: this.inputValue, state: 2, inp: true });
    },
    success(index) {
      this.list[index].state == 1
        ? (this.list[index].state = 2)
        : (this.list[index].state = 1);
    },
    gitImgCode() {
      axios.get("http://localhost:5000/user/getCode").then((res) => {
        console.log(res);
        this.dataImage = res.data.img;
      });
    },
    sumFilter(arr, index) {
      arr.filter((item, index, arrItem) => {
        if (index == 0) {
          item[3];
        }
      });
    },
    sumHeight(arr) {
      var arr1, arr2, arr3;
    },
    oneExport() {
      console.log("oneExport");
    },
    oneUpload() {
      console.log("oneUpload");
    },
  },
};
</script>
