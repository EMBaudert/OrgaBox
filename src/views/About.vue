<template>
  <div class="about">
    <h1>{{ $t('navAbout') }} OrgaBox</h1>
    <h2>Version {{version.version}} (Built at {{version.date}})</h2>
    <p>&copy; 2019 - {{new Date().getFullYear()}} — <a href="mailto:magicm-96@gmx.de"><strong>MagicM</strong></a></p>
    <v-simple-table>
      <thead>
        <tr>
          <th class="text-left">Version number</th>
          <th class="text-left">Description</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="change in changelog" :key="change.number">
          <td>{{ change.number }}</td>
          <td>{{ change.description }}</td>
        </tr>
      </tbody>
    </v-simple-table>
  </div>
</template>

<script>
export default {
  computed: {
    version: function () {
      return this.$store.state.version
    },
    changelog: function () {
      const changes = []
      for (const key in this.$store.state.changelog) {
        changes.unshift({ number: key, description: this.$store.state.changelog[key] })
      }
      return changes
    }
  },
  methods: {

  }
}
</script>

<style scoped>
a {
  color: var(--v-anchor-link) !important;
}
</style>
