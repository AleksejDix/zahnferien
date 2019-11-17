<template>
  <nav
    class="menu bg-white lg:bg-transparent sm:fixed w-full z-10 shadow lg:block lg:shadow-none lg:w-64 fixed left-0 lg:left-auto right-0 lg:right-auto lg:sticky top-0 p-2"
    :class="{
      'menu-open': open
    }">
    <slot/>


    <div class="antialiased ">

  <div class="flex justify-center pr-8">
    <nav id="nav" class="w-56 relative">

      <span
        class="absolute h-10 w-full bg-white rounded-lg shadow ease-out transition-transform transition-medium"
        :style="{ transform: `translateY(calc(100% * ${selected}))` }"
      ></span>

      <div class="nav relative">
        <nuxt-link
          v-for="(value, key, index) in links" :key="key"
          exact
          @click.native="select(index)"
          :to="{name: key}"
          class="relative nav-link py-2 px-3 w-full flex items-center focus:outline-none focus-visible:underline"
        >
          <Icon :name="value.icon" />
          <span
            class="nav-text ml-2 text-sm font-medium transition-all ease-out transition-medium"
          >
            {{value.text}}
          </span>
        </nuxt-link>
      </div>

    </nav>
  </div>
</div>
    <div class="flex justify-end bg-gray-200 p-4 -mx-2 -mb-2 lg:hidden">
      <button class="button" @click="$emit('close')">
        <div class="flex items-center">
          <Icon name="icon-close-circle"/>
          <span class="inline-flex ml-2">Menü schlie­ßen</span>
        </div>
      </button>
    </div>
  </nav>
</template>

<script>
import Icon from './Icon'
import Logo from './Logo'
export default {
  components: {
    Logo,
    Icon
  },
  props: ['open'],
  data() {
    return {
      selected: 0,
      links: {
        index: {
          text: 'Startseite',
          icon: 'icon-home'
        },
        services: {
          text: 'Dienstleistungen',
          icon: 'icon-widget-add'
        },
        // blog: {
        //   text: 'Blog',
        //   icon: 'icon-click-target'
        // },
        contact: {
          text: 'Terminwunsch',
          icon: 'icon-chat-group'
        },
        location: {
          text: 'Standort',
          icon: 'icon-location-pin'
        },
        // certification: {
        //   text: 'Zertifikate',
        //   icon: 'icon-certificate'
        // },
        // workshops: {
        //   text: 'Workshops',
        //   icon: 'icon-work'
        // },
      }
    }
  },
  methods: {
    select (index) {
      console.log(index)
      this.selected = index
    },
    selectUnknown() {
      if (process.server) return
      const active = document.querySelector('.nav .nuxt-link-active')
      if (!active) return
      const index = [...active.parentElement.children].indexOf(active)
      this.selected = index
    }
  },
  mounted() {
    this.selectUnknown()
  }
}
</script>


<style scoped>
.menu {
  transition: 200ms transform ease-in ;
  transform: translate3d(0, -100%, 0)
}

@media (min-width: 1024px) {
  .menu {
  transform: translate3d(0, 0, 0)
  }
}

.menu.menu-open {
  transition:  200ms transform ease-out;
  transform: translate3d(0, 0, 0)
}

.nav-link svg  {
  @apply text-gray-500
}
.nav-link.nuxt-link-active svg  {
  @apply text-blue-400
}

.nav-text {
  @apply text-gray-700
}
.nuxt-link-active .nav-text {
  @apply text-blue-600
}
</style>
