<template>
  <span>
    {{ tag }}
  </span>
</template>

<script>
export default {
  name: "JobTag",
  props: {
    tag: {
      type: String,
      required: true
    }
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
  padding: 8px 14px;
  margin-right: 8px;
  transition: all .3s ease-in-out;
  cursor: pointer;

  &:hover {
    background: hsl(180, 29%, 50%);
    color: #ffffff;
  }
}
</style>