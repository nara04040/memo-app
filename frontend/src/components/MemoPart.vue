<template>
  <div class="memo">
    <div class="act">
      <button class="btn btn-primary btn-block" @click="add()">+ 추가</button>
      <button class="btn btn-primary btn-block" @click="del()">+ 삭제</button>
    </div>
    <ul>
      <li v-for="(d, idx) in state.data" :key="idx">{{ d }}</li>
    </ul>
  </div>
</template>

<script>
import { reactive } from "vue";
import axios from "axios";
export default {
  setup() {
    const state = reactive({
      data: [],
    });

    const add = () => {
      const constent = prompt("내용을 입력해주세요.");

      axios.post("/api/memos", { constent }).then((res) => {
        state.data = res.data;
      });
    };

    const del = () => {
      axios.delete("/api/memos").then((res) => {
        state.data = res.data;
      });
    };

    axios.get("/api/memos").then((res) => {
      state.data = res.data;
    });

    return { state, add, del };
  },
};
</script>

<style lang="scss" scoped>
.memo {
  padding: 0 150px;
  .act {
    padding: 10px 5px 5px 5px;
    text-align: right;
  }
  ul {
    border-top: 2px solid #eee;
    list-style: none;
    padding: 0;
    margin: 0;

    li {
      padding: 15px;
      margin: 10px;
      border: 1px solid #eee;
    }
  }
}
</style>
