<template>
  <div
    class="
      min-h-screen
      flex flex-col
      bg-gray-100
      w-screen
      text-gray-700
      antialiased
      leading-tight
    "
  >
    <TopNavSmart
      :navigation="mainNav"
      :active-main="activeMain"
      :current-title="currentTitle"
    />
    <main
      class="min-h-full flex-grow"
      style="min-height: 30rem"
      role="main"
      aria-label="Inhalt"
    >
      <Nuxt class="!pt-32" />
    </main>
    <!-- <VueAnnouncer /> -->
    <nav class="fixed right-0 top-[20rem] sm:top-[10rem]">
      <a
        href="https://grenzensindrelativ.de"
        class="
          bg-white
          rounded-l-md
          border
          shadow
          flex flex-col
          items-center
          justify-center
          p-2 sm:p-4
          pr-4 sn:pr-6
        "
      >
        <svg
          xmlns="http://www.w3.org/2000/svg"
          class="h-6 w-6 sm:h-8 sm:w-8"
          fill="none"
          viewBox="0 0 24 24"
          stroke="currentColor"
        >
          <path
            stroke-linecap="round"
            stroke-linejoin="round"
            stroke-width="1.5"
            d="M3 12l2-2m0 0l7-7 7 7M5 10v10a1 1 0 001 1h3m10-11l2 2m-2-2v10a1 1 0 01-1 1h-3m-6 0a1 1 0 001-1v-4a1 1 0 011-1h2a1 1 0 011 1v4a1 1 0 001 1m-6 0h6"
          />
        </svg>
        <span class="text-center pt-2 text-xs"
          >Zur<br />Original-<br />Seite</span
        >
      </a>
    </nav>
    <Footer
      :navigation="footerNav"
      :copyright="copyright"
      aria-label="Fußleiste"
    />
  </div>
</template>

<script>
export default {
  async created() {
    this.mainNav = this.$store.getters['navigation/mainNav']
    this.footerNav = this.$store.getters['navigation/footerNav']
    this.copyright = this.$store.getters['navigation/copyright']

    const breadCrumbs = this.$store.getters['navigation/breadCrumbs'](
      this.$route
    )
    this.activeMain =
      breadCrumbs && breadCrumbs.length ? breadCrumbs[0].title : null

    const crumbAnomaly =
      breadCrumbs.length > 1 && breadCrumbs[breadCrumbs.length - 2].children
    const off = crumbAnomaly ? 2 : 1
    const lastCrumb = breadCrumbs[breadCrumbs.length - off]
    this.currentTitle = lastCrumb ? lastCrumb.title : null
  },
  data: () => ({
    mainNav: null,
    footerNav: null,
    copyright: null,
    activeMain: null,
    currentTitle: null,
  }),
}
</script>
