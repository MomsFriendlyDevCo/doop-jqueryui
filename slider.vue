<script lang="js" frontend>
/**
 * 
 */
app.component('jqueryuiSlider', {
	props: {
		min: {type: Number, default: 0},
		max: {type: Number, default: 100},
		disabled: {type: Boolean},
		readonly: {type: Boolean},
		range: {type: Boolean},
		step: {type: Number, default: 1},
		value: {type: Number, required: true},
	},
	mounted() {
		return new Promise((resolve, reject) => {
			$(this.$el).slider({
				disabled: this.disabled,
				min: this.min,
				max: this.max,
				range: this.range,
				step: this.step,
				value: this.value,
				create: resolve,
				slide: (e, ui) => !this.readonly && this.$emit('change', ui.value),
			});
		});
	},
	beforeDestroy() {
		$(this.$el).slider('destroy');
	},
});
</script>

<template>
	<div class="jqueryui-slider ui-input ui-state-default ui-corner-all">
	</div>
</template>
