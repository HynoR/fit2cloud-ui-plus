<template>
  <el-button v-bind="$attrs">
    <slot />
  </el-button>
</template>
<script lang="ts" setup>
import {ElButton} from "element-plus";

defineOptions({
  name: "FuStepButton",
  components: {ElButton}
});

</script>
