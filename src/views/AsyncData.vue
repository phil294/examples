<template>
  <PageLayout title="Async data">
    <p>This page show data loaded via <code>asyncData()</code> on current page component</p>
  </PageLayout>
</template>

<script>
import PageLayout from '@/components/PageLayout';
import { pageEnterEffect, pageLeaveEffect } from '@/effects';

export default {
  mixins: [pageEnterEffect, pageLeaveEffect],

  components: {
    PageLayout,
  },

  /* Demo broken redirect function */
  async asyncData({ redirect }) {
    return redirect({ to: '/vuex' }, 302);
  },
};
</script>
