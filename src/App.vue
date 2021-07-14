<template>
  <div id="app">
    <GridWrapper :header="header" :data="testData" :columns="columns" />
  </div>
</template>

<script>
import GridWrapper from "./components/GridWrapper";

export default {
  name: "App",
  components: {
    GridWrapper,
  },
  data: () => ({
    columns: ["openTime", "issue", "openNumber", "openNumber"],
    header: [
      // 一般
      "时间",
      "期号",
      ["显示号码", "显示大小", "显示单双"],
      "总和 / 形态",
    ],
    testData: [
      {
        lotteryCode: "1008",
        issue: "202107121439",
        openNumber: "6,1,3,6,8",
        openTime: "2021-07-12 23:59:06",
        open: false,
        createdTime: null,
        tenantCode: null,
        lotteryName: null,
        lotteryType: null,
      },
      {
        lotteryCode: "1008",
        issue: "202107121439",
        openNumber: "6,1,3,6,8",
        openTime: "2021-07-12 23:59:06",
        open: false,
        createdTime: null,
        tenantCode: null,
        lotteryName: null,
        lotteryType: null,
      },
      {
        lotteryCode: "1008",
        issue: "202107121439",
        openNumber: "6,1,3,6,8",
        openTime: "2021-07-12 23:59:06",
        open: false,
        createdTime: null,
        tenantCode: null,
        lotteryName: null,
        lotteryType: null,
      },
    ],
  }),
};
</script>

<style>
</style>
