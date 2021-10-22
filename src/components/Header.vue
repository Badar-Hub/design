<template>
  <div class="row justify-between bg-green-14 q-pa-sm q-py-md">
    <div class="row">
      <q-icon color="white" size="md" name="menu" />
      <h5 class="q-mx-sm q-my-auto text-white">Scores</h5>
    </div>

    <q-icon name="search" size="md" color="white" />
  </div>
  <div class="row justify-between bg-green-14 q-px-sm text-white">
    <div
      v-for="(route, index) in getRoutes"
      :key="index"
      :class="`router-link-exact-active`"
      class="router-link-active col col-xs-3 text-center"
    >
      <router-link :to="route.path">
        <h6 class="q-my-sm" @click="onRouteClicked(route)">
          {{ route.name }}
        </h6>
      </router-link>
    </div>

    <div
      :class="$q.screen.gt.sm ? 'text-center ' : 'text-right'"
      class="col-xs-2 q-my-auto q-pr-md"
    >
      <q-icon disabled size="md" name="event" class="cursor-pointer" />
    </div>
  </div>
</template>

<script>
import { ref, computed } from 'vue';
import { useRouter } from 'vue-router';
export default {
  setup(_, context) {
    const router = useRouter();
    const date = ref('21-10-2021');
    const getRoutes = computed(() => {
      return router.options.routes;
    });

    const onRouteClicked = (route) => {
      context.emit('date-changed', route.name);
    };

    return {
      getRoutes,
      date,
      onRouteClicked,
    };
  },
};
</script>

<style lang="scss">
.brdr-b {
  border-bottom: 2px solid;
}
a {
  color: white;
  text-decoration: none;
}
.router-link-exact-active {
  color: white !important;
}
</style>
