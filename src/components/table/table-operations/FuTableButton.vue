<template>
  <el-tooltip :content="label" :disabled="!icon">
    <el-button link v-bind="$attrs" :disabled="disabled">
      <slot></slot>
    </el-button>
  </el-tooltip>
</template>
<script lang="ts" setup>
import {ElButton, ElTooltip} from "element-plus";

defineOptions({ name: "FuTableButton", components: {ElTooltip, ElButton} });
defineProps({
  label: String,
  disabled: Boolean,
  icon: Boolean,
});

</script>
