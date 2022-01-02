<script lang="ts">
import { computed, defineComponent } from "vue";

export default /*#__PURE__*/ defineComponent({
  name: "RadialProgressVue3", // vue component name
  props: {
    width: {
      type: Number,
      default: 80,
    },
    strokeWidth: {
      type: Number,
      default: 6,
    },
    strokeColor: {
      type: String,
      default: "#2e5090",
    },
    innerStrokeColor: {
      type: String,
      default: "#ffaadd",
    },
    fillColor: {
      type: String,
      default: "#E6E6FA",
    },
    roundedStroke: {
      type: Boolean,
      default: false,
    },
    showText: {
      type: Boolean,
      default: true,
    },
    textColor: {
      type: String,
      default: "#222222",
    },
    fontWeight: {
      type: [String, Number],
      default: 900,
    },
    fontSize: {
      type: Number,
      default: 12,
    },

    showPercentSymbol: {
      type: Boolean,
      default: true,
    },
    clockWise: {
      type: Boolean,
      default: true,
    },
    percent: {
      type: Number,
      default: 42,
    },
  },

  setup: (props) => {
    const radius = props.width / 2 - props.strokeWidth * 2;

    const circumference = 2 * Math.PI * radius;

    const offset = computed(() => {
      if (props.clockWise) {
        return circumference - (props.percent / 100) * circumference;
      } else {
        return circumference + (props.percent / 100) * circumference;
      }
    });

    const roundedPercent = computed(() => Math.round(props.percent));

    return {
      radius,
      circumference,
      offset,
      roundedPercent,
    };
  },
});
</script>

<template>
  <svg :width="width" :height="width">
    <circle
      :cx="width / 2"
      :cy="width / 2"
      :r="radius"
      :fill="fillColor"
      :stroke="innerStrokeColor"
      :stroke-width="strokeWidth"
    />

    <circle
      :cx="width / 2"
      :cy="width / 2"
      :r="radius"
      fill="transparent"
      :stroke="strokeColor"
      :stroke-width="strokeWidth"
      :stroke-dasharray="circumference"
      :stroke-dashoffset="offset"
      :stroke-linecap="roundedStroke ? 'round' : 'butt'"
      :class="$style.circle"
    />

    <text
      v-if="showText"
      x="50%"
      y="50%"
      :fill="textColor"
      :style="{
        fontWeight: fontWeight,
        fontSize: `${fontSize}px`,
      }"
      dominant-baseline="middle"
      text-anchor="middle"
    >
      {{ roundedPercent }}{{ showPercentSymbol ? "%" : "" }}
    </text>
  </svg>
</template>

<style module>
.circle {
  transform: rotate(-90deg);
  transform-origin: center;

  transition: 500ms stroke-dashoffset linear;
}
</style>
