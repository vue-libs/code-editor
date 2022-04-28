<template>
  <div>
    <EditorWrapper :config="config" v-model="code" />
  </div>
</template>

<script>
import EditorWrapper from "./components/EditorWrapper.vue";

export default {
  name: "App",
  components: {
    EditorWrapper,
  },
  data() {
    return {
      code: "plain code",
      config: {
        style: "width:800px;height:600px;border:1px solid grey",
        theme: "vs-dark",
        language: "javascript",
      },
    };
  },
};
</script>