<template>
  <div class="grid_container">
    <div class="wrap-record-title grid_header">
      <div
        v-for="(title, index) in header"
        :key="index"
        class="record-title grid_column"
      >
        <div v-if="!Array.isArray(title)" class="cell">{{ title }}</div>
        <div
          v-for="innertitle in title"
          v-else
          :key="innertitle"
          class="cell innerTitle"
        >
          <div>{{ innertitle }}</div>
        </div>
      </div>
    </div>

    <div class="wrap-record-data grid_body">
      <div v-for="(item, i) in data" :key="i" class="record-data grid_row">
        <!--
        <div class="grid_column">{{ item.openTime }}</div>
        <div class="grid_column">{{ item.issue }}</div>
        <div class="grid_column">{{ item.openNumber }}</div>
        <div class="grid_column">{{ item.openNumber }}</div>
        -->

        <div
          v-for="(column, index) in columns"
          :key="`${column}-${index}`"
          class="grid_column"
        >
          {{ item[column] }}
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "GridWrapper",
  props: {
    header: {
      type: Array,
      required: true,
    },
    data: {
      type: Array,
      required: true,
    },
    columns: {
      type: Array,
      required: true,
    },
  },
  data: () => ({}),
};
</script>

<style rel="stylesheet/scss" lang="scss" scoped>
@mixin set_grid_center {
  display: grid;
  place-content: center;
}

@mixin set_border_BR {
  border-bottom: 1px solid black;
  border-right: 1px solid black;
}

.grid_container {
  // padding: 1px;
}

.grid_header {
  @include set_border_BR;

  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(10px, 1fr));

  background: rgb(226, 226, 226);

  > .grid_column {
    @include set_grid_center;

    border-top: 1px solid black;
    border-left: 1px solid black;

    grid-auto-flow: column;
    height: 50px;

    .innerTitle {
      border: 1px solid black;
      border-radius: 5px;
      padding: 5px 10px;
    }

    .innerTitle + .innerTitle {
      margin-left: 10px;
    }
  }
}

.grid_body {
  > .record-data {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(10px, 1fr));
    border-left: 1px solid black;

    > div {
      @include set_border_BR;
      @include set_grid_center;
      height: 50px;
    }
  }
}
</style>
