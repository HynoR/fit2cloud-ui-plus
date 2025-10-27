<template>
  <div :class="[
  'fu-speed-dial-button',
  'el-button',
  'el-button--' + type,
  {
    'fu-speed-dial-button--rotate': rotate,
    'is-disabled': disabled,
    'is-active': active,
  },]" :style="{
    width: size,
    height: size,
    backgroundColor: backgroundColor,
    color: color,
    fontSize: fontSize
  }">
    <slot>
      <el-icon>
        <component :is="resolvedIcon" />
      </el-icon>
    </slot>
  </div>
</template>

<script setup lang="ts">
import {computed} from "vue";
import {ElIcon} from "element-plus";
import {Close, Plus} from "@element-plus/icons-vue";
import { validateType } from "@/tools/theme"

defineOptions({
  name: "FuSpeedDialButton",
  components: {ElIcon}
});
const props = defineProps({
  type: {
    type: String,
    default: "default",
    validator: validateType
  },
  rotate: Boolean,
  disabled: Boolean,
  active: Boolean,
  icon: [String, Object, Function],
  size: {
    type: String,
    default: "32px"
  },
  backgroundColor: String,
  color: String,
  fontSize: String
})

const iconMap = {Plus, Close}
const resolvedIcon = computed(() => {
  if (typeof props.icon === "string") {
    return iconMap[props.icon as keyof typeof iconMap] || props.icon
  }
  return props.icon
})
</script>
