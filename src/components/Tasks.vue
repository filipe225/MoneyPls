<template>
  <v-card transition="slide-x-reverse-transition card-main-bgcolor" >
    <v-toolbar class="card-main-bgcolor">
		<v-toolbar-title><h3>Tasks</h3></v-toolbar-title>
		<v-spacer></v-spacer>
		<v-btn icon>
			<v-icon>add_circle</v-icon>
		</v-btn>
    </v-toolbar>

	<v-card v-if="!items" style="height: 100%">
		<v-card-text>
			<p class="text-xs-center">COMING SOON</p>
		</v-card-text>
	</v-card>

    <v-list class="hidden">
		<template v-for="(item, index) in items">
			<v-list-tile :key="item.title" avatar ripple>
				<v-list-tile-content>
					<v-list-tile-title>{{ item.title }}</v-list-tile-title>
					<v-list-tile-sub-title>{{ item.content }}</v-list-tile-sub-title>
				</v-list-tile-content>

				<v-list-tile-action>
					<v-list-tile-action-text>{{ item.date }}</v-list-tile-action-text>
					<v-list-tile-action-text>{{ item.deadline }}</v-list-tile-action-text>
					<v-list-tile-action-text>{{ item.status }}</v-list-tile-action-text>
				</v-list-tile-action>
			</v-list-tile>
			<v-divider v-if="index + 1 < items.length" :key="index"></v-divider>
		</template>
    </v-list>
  </v-card>
</template>

<script>
export default {
  props: ["userAssignedTasks"],

  data() {
    return {};
  },

  computed: {
    items() {
      return this.userAssignedTasks;
    }
  },

  created: function() {},

  methods: {
    toggle(index) {
      const i = this.selected.indexOf(index);

      if (i > -1) {
        this.selected.splice(i, 1);
      } else {
        this.selected.push(index);
      }
    }
  }
};
</script>