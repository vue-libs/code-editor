<template>
  <div>
    <MonacoEditor
      v-bind="editorConfigObject"
      :value="value"
      @change="updatedCode"
    />
  </div>
</template>

<script>
import MonacoEditor from "vue-monaco";
import { DEFAULT_EDITOR_CONFIG } from "../util/constants";

export default {
  components: {
    MonacoEditor,
  },
  props: {
    config: { type: Object, required: true },
    value: { type: String },
  },
  mounted() {
    this.preloadConfigs();
  },
  data() {
    const defaultEditorConfig = DEFAULT_EDITOR_CONFIG;
    return {
      editorConfigObject: {},
      defaultEditorConfig,
    };
  },
  methods: {
    updatedCode(newValue) {
      this.$emit("input", newValue);
    },
    preloadConfigs() {
      this.editorConfigObject = { ...this.defaultEditorConfig, ...this.config };
    },
  },
};
</script>
