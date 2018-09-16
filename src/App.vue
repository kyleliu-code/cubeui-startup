<template>
  <div id="app">
    <div class="header">
      <h1 class="title" @click="showPicker"></h1>
      <span>{{source}}赛事</span>
      <i class="cubeic-select" :class="{down: toDown}"></i>
    </div>
    <div class="navigator">
        <ul class="nav-list">
            <li v-for="(item, index) in tabList" :key="index" @click="switchTab(index)" :class="{active: currentPage === index}">{{ item.txt }}</li>
        </ul>
    </div>
  </div>
</template>
<script>
	import { ENDED, CONCERN, LIVE} from '@/common/config/tabs.js';
  export default {
    name: "app",
    data() {
      return {
        source: "soccer",
        currentPage: 1,
        toDown: false,
        tabList: [
            {
                txt: '已结束',
                type: ENDED
            },
            {
                txt: '我的关注',
                type: CONCERN
            },
            {
                txt: '直播中',
                type: LIVE
            }
        ]
      };
    },
    methods: {
        showPicker() {},
        switchTab(index) {
					this.currentPage = index;
				}
    }
  }

</script>
<style lang="stylus" scoped>
@import './common/stylus/mixin.styl'
html, body, #app
	height: 100%
	text-align: center
#app
	background-color: color_grey
	.header
		color: white
		background-color #15191d
		.title
			padding: 20px 0
			font-size: 16px
			color: white
			display: inline-block
			.down
				display: inline-block
				tranform: rotate(180deg)
			.navigator
				position: relative 
				padding-bottom: 12px
				font-size 12px
				.nav-list
					display: flex
					justify-content: space-around
					li
						width: 60px
						color: #e0e4e8
						&.active
							color: white
</style>
