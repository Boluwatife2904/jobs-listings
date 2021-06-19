<template>
  <span class="filter-item">
    <span class="name">{{ name }}</span>
    <span class="close" @click="removeFilter">X</span>
  </span>
</template>

<script>
export default {
  props: {
    name: {
      type: String,
      required: true,
    },
  },
  setup(props, context) {
    const removeFilter = () => {
      context.emit("remove-filter", props.name)
    }
    return { removeFilter }
  }
};
</script>

<style lang="scss" scoped>
.filter-item {
  display: inline-flex;
  margin: 8px 8px 8px 0;

  span {
    background: hsl(180, 31%, 95%);
    color: hsl(180, 29%, 50%);
    font-weight: 600;
    font-size: 12px;
  }

  .name {
    padding: 8px 14px 6px;
    border-radius: 4px 0px 0px 4px;
  }

  .close {
    background: hsl(180, 29%, 50%);
    padding: 8px 8px 6px;
    color: #ffffff;
    cursor: pointer;
    border-radius: 0px 4px 4px 0px;
    transition: all 0.3s;

    &:hover {
      background: hsl(180, 14%, 20%);
    }
  }
}
</style>