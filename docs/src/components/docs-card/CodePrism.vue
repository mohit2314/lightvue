<template>
  <pre ref="code" :class="languageClass"><code><slot></slot></code></pre>
</template>

<script>
import Prism from "prismjs";
import "./prism.css";
// import "./prism-old.css";

export default {
  props: {
    lang: {
      type: String,
      default: "markup",
    },
  },
  computed: {
    languageClass() {
      return "language-" + this.lang;
    },
  },
  mounted() {
    Prism.highlightElement(this.$el.children[0]);
  },
};
</script>
