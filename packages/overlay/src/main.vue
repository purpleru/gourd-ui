<template>
  <div class="gourd-overlay" :style="overlay" v-show="value" @click="clickHandler" @touchmove.prevent @mousewheel.prevent>
    <slot></slot>
  </div>
</template>

<script>
export default {
	name: 'GourdOverlay',
	model: {
		prop: 'value',
		event: 'change'
	},
	props: {
		value: Boolean,
		region: Boolean,
		color: {
			type: String,
			default: ''
		}
	},
	methods: {
		clickHandler(event) {
			this.$emit('click', event);
		}
	},
	computed: {
		overlay() {
			var style = {};

			if (this.region) {
				style.position = 'absolute';
			}

			if (this.color) {
				style.backgroundColor = this.color;
			}

			return style;
		}
	}
};
</script>
