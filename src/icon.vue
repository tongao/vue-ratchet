<template>
	<span class="icon" :class="setClass"></span>
</template>

<script>
	export default {
		name: 'icon',
		props:{
	      icon: {
	      	type: String,
	      	required: true
	      },
	      classes: ''
	    },
	    data(){
	    	return {
	    		classData: ['icon-'+this.icon]
	    	}
	    },
	    computed: {
	    	setClass: function() {
	    		return this.classData.concat(this.classes ? this.classes.split(' ') : []);
	    	}
	    }
	}
</script>

<style lang="sass">
	@import './scss/icons';
</style>
