<template>
  <span @click="setFilter">
    {{ tag }}
  </span>
</template>

<script>
export default {
  name: "JobTag",
  emits: ['set-filter'],
  props: {
    tag: {
      type: String,
      required: true
    }
  },
  setup(props, context) {
    const setFilter = () => {
      context.emit("set-filter", props.tag)
    }
    return { setFilter }
  }
}
</script>

<style lang="scss" scoped>
span {
  border-radius: 4px;
  background: hsl(180, 31%, 95%);
  color: hsl(180, 29%, 50%);
  font-weight: 600;
  font-size: 12px;
  padding: 8px 14px 6px;
  margin: 8px 8px 8px 0;
  transition: all .3s ease-in-out;
  cursor: pointer;
  display: inline-block;

  &:hover {
    background: hsl(180, 29%, 50%);
    color: #ffffff;
  }
}
</style>