<template>
  <span class="badge" :class="mode">
    <slot></slot>
  </span>
</template>

<script>
export default {
  name: "JobBadge",
  props: {
    mode: {
      type: String,
      required: true
    }
  }
}
</script>

<style lang="scss">
.badge {
  font-size: 10px;
  text-transform: uppercase;
  padding: 6px 8px 4px;
  color: #ffffff;
  font-weight: 600;
  border-radius: 20px;
  margin-right: 6px;

  &.new {
    background: hsl(180, 29%, 50%);
  }

  &.featured {
    background: hsl(180, 14%, 20%);
  }
}
</style>