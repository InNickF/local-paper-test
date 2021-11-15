<template>
  <div>
    <v-navigation-drawer
      v-model="drawer"
      class="glass-effect"
      :mini-variant="miniVariant"
      :expand-on-hover="miniVariant"
      :mini-variant-width="64"
      clipped
      fixed
      floating
      app
    >
      <v-list class="py-2 px-2">
        <v-list-item
          v-for="(item, i) in items"
          :key="i"
          :to="item.to"
          router
          exact
          class="mb-1"
        >
          <v-list-item-action>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title v-text="item.title" />
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>

    <v-app-bar class="px-1 glass-effect" clipped-left fixed app>
      <v-btn
        class="d-none d-lg-inline-flex d-xl-inline-flex"
        icon
        color="primary"
        @click.stop="miniVariant = !miniVariant"
        ><v-icon>mdi-menu</v-icon></v-btn
      >
      <v-btn
        class="mobile-drawer-btn d-lg-none d-xl-none"
        icon
        @click.stop="showDrawer()"
        ><v-icon>mdi-menu</v-icon></v-btn
      >
      <v-toolbar-title>
        <LpLogo />
      </v-toolbar-title>

      <v-spacer />

      <LpNavItems :links="links" />
      <LpUserButton />

      <v-btn
        class="mobile-drawer-btn d-lg-none d-xl-none"
        icon
        @click.stop="rightDrawer = !rightDrawer"
      >
        <v-icon>mdi-dots-horizontal</v-icon>
      </v-btn>
    </v-app-bar>

    <v-navigation-drawer
      v-model="rightDrawer"
      class="glass-effect"
      fixed
      floating
      app
      right
      disable-resize-watcher
    >
      <div class="mobile-drawer-content">
        <div>
          <v-list class="py-2 px-2">
            <v-list-item v-for="(link, i) in links" :key="i" class="mb-1">
              <v-list-item-content>
                <v-list-item-title v-text="link" />
              </v-list-item-content>
            </v-list-item>
          </v-list>
        </div>
        <div>
          <v-list-item>
            <v-list-item-content>
              <v-list-item-title
                ><p class="logout">Logout</p></v-list-item-title
              >
            </v-list-item-content>
          </v-list-item>
        </div>
      </div>
    </v-navigation-drawer>
  </div>
</template>
<script>
import LpLogo from '~/components/LpLogo.vue'
export default {
  name: 'LpNavigation',
  components: { LpLogo },
  data() {
    return {
      drawer: null, // Must start in null... wtf
      miniVariant: true,
      rightDrawer: false,
      items: [
        {
          icon: 'mdi-view-dashboard',
          title: 'Dashboard',
          to: '/',
        },
        {
          icon: 'mdi-chart-areaspline',
          title: 'Investments',
          to: '/investments',
        },
        {
          icon: 'mdi-distribute-horizontal-center',
          title: 'Distribution',
          to: '/distribution',
        },
        {
          icon: 'mdi-file-document',
          title: 'Documents',
          to: '/documents',
        },
        {
          icon: 'mdi-badge-account',
          title: 'Entities',
          to: '/entities',
        },
        {
          icon: 'mdi-bank',
          title: 'Bank Acct',
          to: '/bank-acct',
        },
        {
          icon: 'mdi-inbox-arrow-down',
          title: 'Inbox',
          to: '/inbox',
        },
      ],
      links: [
        'Home',
        'Investment',
        'Real State',
        'Find art',
        'About us',
        'Information',
      ],
    }
  },
  methods: {
    showDrawer() {
      this.drawer = !this.drawer
      this.miniVariant = false
    },
  },
}
</script>
<style scoped>
* >>> .v-app-bar__nav-icon {
  box-shadow: 0px 0px 8px #3333331a;
}
.v-sheet.v-app-bar.v-toolbar:not(.v-sheet--outlined) {
  box-shadow: 0px 0px 30px #33333317 !important;
}
header {
  border-radius: 50px !important;
  margin: 10px !important;
}
nav {
  box-shadow: 0px 0px 15px #33333317 !important;
  margin: 20px 10px;
  border-radius: 30px;
  height: calc(100vh - 100px) !important;
}

@media (max-width: 1246px) {
  nav {
    margin: 10px;
  }
}

.v-navigation-drawer__content {
  display: flex !important;
  flex-direction: column !important;
  justify-content: space-between !important;
}
.mobile-drawer-btn {
  margin-left: -14px;
}
.v-list-item {
  border-radius: 100px !important;
  overflow: hidden !important;
  padding: 0 12px;
}

.mobile-drawer-content {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  height: 100%;
  padding: 0 12px;
}
.logout {
  color: rgb(255, 70, 70);
}
</style>
