<template>
	<div>
		<img v-for="(item, index) in skin" :key="index" v-lazyload="item.img" @click="toSkin(item.url)">
	</div>
</template>

<script>
import {mapState} from 'vuex'
export default {
	head () {
    return {
      title: `皮肤鉴赏`
    }
	},
	data () {
		return {
			skin: []
		}
	},
	methods: {
		toSkin(url) {
			location.href = url
		}
	},
	beforeMount() {
		this.$store.dispatch('getSkin').then(res => {
			this.skin = res
		})
	}
}
</script>

