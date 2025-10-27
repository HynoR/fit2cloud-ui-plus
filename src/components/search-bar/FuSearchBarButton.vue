<template>
  <el-tooltip :content="tooltip" :disabled="!tooltip">
    <el-button class="fu-search-bar-button" circle :size="configSize" :icon="resolvedIcon" v-bind="$attrs"/>
  </el-tooltip>
</template>


<script setup lang="ts">
import {computed} from "vue";
import {validateSize} from "@/tools/size";
import {useSize} from "@/hooks";
import {ElButton, ElTooltip} from "element-plus";
import {Close, Refresh} from "@element-plus/icons-vue";

defineOptions({name: "FuSearchBarButton", components: {ElTooltip, ElButton}});

const props = defineProps({
  size: {
    type: String,
    validator: validateSize
  },
  tooltip: String,
  icon: [String, Object, Function]
})

const configSize = useSize()

const iconMap = {Close, Refresh}
const resolvedIcon = computed(() => {
  if (typeof props.icon === "string") {
    return iconMap[props.icon as keyof typeof iconMap] || props.icon
  }
  return props.icon
})
</script>
