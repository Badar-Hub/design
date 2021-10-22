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
        <h6 class="q-my-sm">
          {{ route.name }}
        </h6>
      </router-link>
      <!-- <q-btn
        flat
        :size="$q.screen.gt.sm ? '20px' : '18px'"
        :label="route.name"
        :to="route.path"
      /> -->
    </div>

    <div
      :class="$q.screen.gt.sm ? 'text-center ' : 'text-right'"
      class="col-xs-2 q-my-auto q-pr-md"
    >
      <q-icon size="lg" name="event" class="cursor-pointer">
        <q-popup-proxy transition-show="scale" transition-hide="scale">
          <q-date v-model="date" mask="YYYY-MM-DD HH:mm">
            <div class="row items-center justify-end">
              <q-btn v-close-popup label="Close" color="primary" flat />
            </div>
          </q-date>
        </q-popup-proxy>
      </q-icon>
    </div>
  </div>
  <div class="row bg-white">
    <div class="col-xs-4 text-center">
      <q-btn flat size="16px" label="All" class="q-my-sm" />
    </div>
    <div class="col-xs-4 text-center">
      <q-btn flat size="16px" label="Live" class="q-my-sm" />
    </div>
    <div class="col-xs-4 text-center">
      <q-btn flat size="16px" label="Favorites" class="q-my-sm" />
    </div>
  </div>
</template>

<script>
import { ref, computed } from 'vue';
import { useRouter } from 'vue-router';
export default {
  setup() {
    const router = useRouter();
    const date = ref('2019/03/01');

    const getRoutes = computed(() => {
      return router.options.routes;
    });

    return {
      getRoutes,
      date,
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
