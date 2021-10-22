<template>
  <div v-for="(a, i) in data" :key="i" :class="$q.screen.gt.xs ? 'q-ma-sm' : 'q-my-sm'">
    <q-card class="q-mx-xs">
      <q-card-section>
        <div class="row justify-between full-width q-my-auto items-center">
          <p class="q-my-md">
            Country:
            <strong class="q-mx-md">{{ a.name.toUpperCase() }}</strong>
          </p>
          <q-icon name="star" size="sm" />
        </div>
        <div
          class="row justify-between full-width q-my-auto items-center q-px-md"
        >
          <p class="q-my-sm">
            End: <strong class="q-mx-md">{{ a.start.toUpperCase() }}</strong>
          </p>
          <strong>1</strong>
        </div>
        <separator class="q-my-sm" bgcl="#c7c7c7" />
        <div
          class="row justify-between full-width q-my-auto items-center q-px-md"
        >
          <p class="q-my-sm">
            End: <strong class="q-mx-md"> {{ a.center.toUpperCase() }}</strong>
          </p>
          <strong> 1</strong>
        </div>
        <separator class="q-my-sm" bgcl="#c7c7c7" />
        <div
          class="row justify-between full-width q-my-auto items-center q-px-md"
        >
          <p class="q-my-sm">
            End: <strong class="q-mx-md"> {{ a.end.toUpperCase() }}</strong>
          </p>
          <strong> 1</strong>
        </div>
      </q-card-section>
    </q-card>
  </div>
</template>

<script>
import Separator from './Separator.vue';
export default {
  components: { Separator },
  props: {
    data: {
      type: Array,
      default: () => [
        { name: 'France', start: 'start', center: 'center', end: 'end' },
        { name: 'Afrique', start: 'start', center: 'center', end: 'end' },
        { name: 'Pakistan', start: 'start', center: 'center', end: 'end' },
      ],
    },
  },
};
</script>

<style lang="scss"></style>
