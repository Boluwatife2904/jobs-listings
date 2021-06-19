<template>
  <div class="job-item" :class="{ featured: job.featured }">
    <div class="job-information">
      <img :src="job.logo" :alt="job.company" class="company-logo" />
      <div class="job-content">
        <div class="header">
          <h3 class="company-name">{{ job.company }}</h3>
          <job-badge mode="new" v-if="job.new">new!</job-badge>
          <job-badge mode="featured" v-if="job.featured">featured</job-badge>
        </div>
        <h6 class="job-position">{{ job.position }}</h6>
        <div class="other-information">
          <span>{{ job.postedAt }}</span>
          <span>{{ job.contract }}</span>
          <span>{{ job.location }}</span>
        </div>
      </div>
    </div>
    <div class="job-tags">
      <job-tag v-for="tag in job.tags" :key="tag" :tag="tag" @set-filter="setFilter"></job-tag>
    </div>
  </div>
</template>

<script>
import JobBadge from "./JobBadge.vue";
import JobTag from "./JobTag.vue";

export default {
  name: "JobItem",
  components: { JobBadge, JobTag },
  emits: ['set-filter'],
  props: {
    job: {
      type: Object,
      required: false,
    },
  },
  setup(_, context) {
    const setFilter = (tag) => {
      context.emit("set-filter", tag)
    }
    return { setFilter }
  }
};
</script>

<style lang="scss">
.job-item {
  display: flex;
  justify-content: space-between;
  align-items: center;
  background: #ffffff;
  border-radius: 6px;
  margin-bottom: 30px;
  padding: 25px 15px 25px 30px;
  box-shadow: 2px 4px 26px 1px rgba(91, 164, 164, 0.2);
  position: relative;

  &.featured {
    border-left: 4px solid hsl(180, 29%, 50%);
  }

  .job-information {
    display: flex;
    flex-shrink: 0;

    img {
      margin-right: 15px;

      @media screen and (max-width: 576px) {
        height: 60px;
        width: 60px;
        position: absolute;
        top: -30px;
      }
    }

    .job-content {
      .header {
        display: flex;
        align-items: center;
        margin-bottom: 10px;

        .company-name {
          margin-right: 10px;
          color: hsl(180, 29%, 50%);
          font-size: 16px;
        }
      }

      .job-position {
        font-size: 15px;
        margin-bottom: 8px;
        font-weight: 600;

        &:hover {
          color: hsl(180, 29%, 50%);
        }
      }

      .other-information {
        span {
          color: hsl(180, 8%, 52%);
          font-weight: 500;
          font-size: 13px;
          margin-right: 30px;
          position: relative;

          &::before {
            position: absolute;
            content: "";
            height: 3px;
            width: 3px;
            background: hsl(180, 8%, 52%);
            border-radius: 50%;
            top: 4px;
            right: -15px;

            @media screen and (max-width: 576px) {
              right: -11px;
            }
          }

          &:last-child {
            &::before {
              display: none;
            }
          }

          @media screen and (max-width: 576px) {
            margin-right: 20px;
          }
        }
      }
    }

    @media screen and (max-width: 779px) {
      width: 100%;
      padding-bottom: 20px;
      margin-bottom: 20px;
      border-bottom: 1px solid rgba(123, 142, 142, 0.5);
    }
  }

  @media screen and (max-width: 779px) {
    justify-content: flex-start;
    align-items: flex-start;
    flex-direction: column;
  }

  @media screen and (max-width: 576px) {
    padding-top: 50px;
    margin-bottom: 50px;
  }
}
</style>