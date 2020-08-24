<template>
  <v-ons-page>
    <v-ons-toolbar>
      <div class="center">{{ title }}</div>
    </v-ons-toolbar>

    <v-ons-tabbar position="auto"
      :tabs="tabs"
      :visible="true"
      :index.sync="activeIndex"
    >
    </v-ons-tabbar>
  </v-ons-page>
</template>

<script>
  import settingsPage from 'Settings';
  import homePage from 'Home';
  import newsPage from 'News';

  export default {
    data() {
      return {
        activeIndex: 0,
        tabs: [
	  {
	    icon: this.md() ? null : 'ion-ios-home',
	    label: '予定を作る',
	    page: homePage
	  },
	  {
	    icon: this.md() ? null : 'ion-ios-bell',
	    label: 'マイカレンダー',
	    page: newsPage,
	    badge: 7
	  },
	  {
	    icon: this.md() ? null : 'ion-ios-settings',
	    label: '予定を探す',
	    page: settingsPage
	  }
        ]
      };
    },
    methods: {
      md() {
        return this.$ons.platform.isAndroid();
      }
    },
    computed: {
      title() {
        return this.tabs[this.activeIndex].label;
      }
    },
    components: { homePage, settingsPage, newsPage }
  }
</script>
