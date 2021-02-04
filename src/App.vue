<template>
  <div class="container">
    <column-list :list="list"></column-list>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import "bootstrap/dist/css/bootstrap.min.css";
import ColumnList, { ColumnProps } from "./components/ColumnList.vue";

const testData: ColumnProps[] = [
  {
    id: 1,
    title: "test1的专栏",
    description: "test1专栏",
    avatar: require("@/assets/logo.png"),
  },
  {
    id: 2,
    title: "test2的专栏",
    description: "test2专栏",
    avatar: require("@/assets/logo.png"),
  },
  {
    id: 3,
    title: "test3的专栏",
    description: "test3专栏",
  },
  {
    id: 4,
    title: "test4的专栏",
    description: "test4专栏",
    avatar: require("@/assets/logo.png"),
  },
];

export default defineComponent({
  name: "App",
  components: {
    ColumnList,
  },
  setup() {
    return {
      list: testData,
    };
  },
});
</script>

<style>
</style>
