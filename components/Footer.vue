<template>
  <footer class="w-full bg-primary-700 text-primary-200 bottom-0">
    <div class="container m-auto px-4 md:px-8 py-10 pb-16 lg:pb-10">
      <div class="grid lg:grid-cols-2">
        <div
          v-for="col in navigation"
          :key="col.title"
          class="flex flex-col pb-8"
        >
          <h3 class="text-xs uppercase text-primary-200 font-bold pb-3">{{ col.title }}</h3>
          <div>
            <div
              v-for="row in col.children"
              :key="row.title"
              class="flex flex-col pb-1 text-primary-300"
            >
              <nuxt-link v-if="row.url" :to="row.url" class="hover:underline hover:text-white">
                {{ row.title }}
              </nuxt-link>
            </div>
          </div>
        </div>
        <!-- <div class="flex flex-col pb-8">
          <h3 class="text-xs uppercase text-primary-200 font-bold pb-3">Anmeldung zum Newsletter</h3>
          <form @click.prevent="() => {}" class="flex flex-col">
            <p class="text-primary-300 text-sm">Melde dich hier zu unserem Newsletter an, um über aktuelle Events und Projekte auf dem laufenden zu bleiben.</p>
            <input type="email" aria-label="E-Mail für Newsletteranmeldung" name="email" class="rounded mt-3 py-3 px-4 bg-primary-400 text-primary-900 placeholder-black focus:bg-primary-200" placeholder="Deine E-Mail">
            <button name="submit" type="submit" class="rounded bg-primary-900 mt-2 py-3 px-4 text-white font-bold tracking-wide" aria-label="zum Newsletter anmelden">Anmelden</button>
          </form>
        </div> -->
      </div>
      <div class="flex">
        <div class="text-sm flex grow">
          {{ copyright }}
        </div>
        <social-icons class="flex justify-end items-center text-gray-300" />
      </div>
    </div>
  </footer>
</template>

<script>
export default {
  props: {
    navigation: { type: Array, default: () => [], required: true },
    copyright: { type: String, required: true }
  }
}
</script>

<style lang="postcss">
footer .link-active {
  @apply font-bold text-white;
}
</style>
