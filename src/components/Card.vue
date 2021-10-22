<template>
  <div
    v-for="(a, i) in data"
    :key="i"
    :class="$q.screen.gt.xs ? 'q-ma-sm' : 'q-my-sm'"
  >
    <q-card class="q-mx-xs">
      <q-card-section>
        <div class="row justify-between full-width q-my-auto items-center">
          <p class="q-my-md">
            Country:
            <strong class="q-mx-md">{{ a.country + ' - ' + a.name }}</strong>
          </p>
          <q-icon
            color="green"
            :name="a.isFavorite ? 'star' : 'star_border'"
            size="sm"
          />
        </div>
        <div v-for="(match, i) in a.matches" :key="i">
          <div
            class="row justify-between full-width q-my-auto items-center q-px-md"
          >
            <div class="col-xs-2">
              End:
            </div>
            <div class="col-xs-8">
              <p
                :class="
                  match.teamOne.status === 'winner' ? 'text-weight-bolder' : ''
                "
                class="q-my-sm"
              >
                <span class="q-mx-md">{{ match.teamOne.name }}</span>
              </p>
              <p
                :class="
                  match.teamTwo.status === 'winner' ? 'text-weight-bolder' : ''
                "
              >
                <span class="q-mx-md">{{ match.teamTwo.name }}</span>
              </p>
            </div>
            <div class="col-xs-2">
              <p class="q-my-sm">
                <span>{{ match.teamOne.goals }}</span>
              </p>
              <p class="q-my-sm">
                <span>{{ match.teamTwo.goals }}</span>
              </p>
            </div>
          </div>
          <separator class="q-my-sm" bgcl="#c7c7c7" />
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
    },
  },
};
</script>

<style lang="scss"></style>
