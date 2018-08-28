<template>
  <div id="sidebar-item">
    <font-awesome-icon id="item-icon" :icon="getIcon(item)"></font-awesome-icon>
    {{item.title}}
  </div>
</template>

<script>
import { library } from "@fortawesome/fontawesome-svg-core";
import {
  faHome,
  faFile,
  faCode,
  faEnvelope,
  faQuestion
} from "@fortawesome/free-solid-svg-icons";

var _ = require("underscore");

_([faHome, faFile, faCode, faEnvelope, faQuestion]).each(icon =>
  library.add(icon)
);

export default {
  name: "SidebarItem",
  props: {
    item: {
      type: Object,
      required: true
    }
  },
  data() {
    return {
      icons: {
        home: faHome,
        resume: faFile,
        github: faCode,
        contact: faEnvelope,
        default: faQuestion
      }
    };
  },
  methods: {
    getIcon(item) {
      let key = item.title.toLowerCase() || "default";
      return this.icons[key];
    }
  }
};
</script>

<style lang="scss" scoped>
#item-icon {
  width: 50px;
}
</style>
