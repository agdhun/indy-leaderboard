<template>
  <section class="row mt-5">
    <table class="table">
      <thead>
        <tr>
          <th width="40">&nbsp;</th>
          <th>Title</th>
          <th>Type</th>
          <th>MaxValue</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(leaderboard, idx) in achievements" :key="idx">
          <td><img :src="leaderboard.Image" /></td>
          <td>{{ leaderboard.Title }}</td>
          <td>{{ leaderboard.Type == 0 ? 'Boolean' : 'Progressive' }}</td>
          <td>{{ leaderboard.Type == 0 ? '-' : leaderboard.MaxValue }}</td>
        </tr>
      </tbody>
    </table>
  </section>
</template>

<script>
import { getAchievements, listenForNewAchievement } from '../actions/gameboard'

export default {
  name: 'Achievements',
  data() {
    return { achievements: {}, eventListener: null }
  },
  async mounted() {
    this.getAchievements()
    this.eventListener = await listenForNewAchievement(this.getAchievements)
  },
  beforeDestroy() {
    if (this.eventListener) {
      this.eventListener.unsubscribe()
    }
  },
  methods: {
    async getAchievements() {
      const achievements = await getAchievements()
      this.$set(this, 'achievements', achievements)
    },
  },
}
</script>
