<template>
<div id="sidebar">
 <b-tabs id="sidebar-items" pills vertical >
    <b-tab v-for="item in items" :key="item.id">
      <template slot="title">
        <SidebarItem v-bind:item="item"/>
      </template>
        <component :is="item.title"/>
    </b-tab>
  </b-tabs>
</div>
</template>

<script>
import SidebarItem from "./SidebarItem";
import Home from "./Home";
import btabs from "bootstrap-vue/es/components/tabs/tabs";
import btab from "bootstrap-vue/es/components/tabs/tab";

export default {
  name: "Sidebar",
  components: {
    SidebarItem,
    Home,
    btabs,
    btab
  },
  data() {
    return {
      items: [
        {
          id: 0,
          title: "Home"
        },
        {
          id: 1,
          title: "Resume"
        },
        {
          id: 2,
          title: "Github"
        },
        {
          id: 3,
          title: "Contact"
        }
      ]
    };
  }
};
</script>

<style lang="scss" scoped>
div.col-auto {
  width: 300px;
}
#sidebar-item {
  width: 100%;
  align-content: left;
  margin-left: 1px;
  padding-left: 1px;
}
</style>
