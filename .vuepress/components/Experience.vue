<template>
<div id="experience">
<span v-for="pos in positions">
    <h3><b>{{ pos.title }}</b></h3>
    <h3>{{ pos.company }}</h3>
    <ul>
        <li><b>{{ pos.location }}</b></li>
        <li><b>{{ pos.period }}</b></li>
        <li><b>Tech: </b>{{ pos.tech }}</li>
        <li><b>Projects:</b>
            <ul>
                <li v-for="proj in pos.projects">
                    {{ proj }}
                </li>
            </ul>
        </li>
    </ul>
</span>
</div>
</template>

<script>
export default {
  name: "Experience",
  computed: {
    positions() {
      return this.$page.frontmatter.positions || [];
    }
  }
};
</script>
