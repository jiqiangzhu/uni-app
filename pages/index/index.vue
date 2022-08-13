<template>
	<view class="container">
		<!-- <view class="intro">本项目已包含uni ui组件，无需import和注册，可直接使用。在代码区键入字母u，即可通过代码助手列出所有可用组件。光标置于组件名称处按F1，即可查看组件文档。</view>
		<text class="intro">详见：</text>
		<uni-link :href="href" :text="href"></uni-link> -->
		<uni-section title="自定义卡片内容" type="line">
			<uni-card title="基础卡片" sub-title="副标题" extra="额外信息" padding="10px 0" :thumbnail="avatar">
				<template v-slot:title>
					<uni-list>
						<uni-list-item :show-switch="true" title="自定义标题" />
					</uni-list>
				</template>
				<image style="width: 100%;" :src="cover"></image>
				<text
					class="uni-body uni-mt-5">卡片组件通用来显示完整独立的一段信息，同时让用户理解他的作用。例如一篇文章的预览图、作者信息、时间等，卡片通常是更复杂和更详细信息的入口点。</text>
				<view slot="actions" class="card-actions">
					<view class="card-actions-item" @click="actionsClick('share')">
						<uni-icons type="pengyouquan" size="18" color="#999"></uni-icons>
						<text class="card-actions-item-text">分享</text>
					</view>
					<view class="card-actions-item" @click="actionsClick('like')">
						<uni-icons type="heart" size="18" color="#999"></uni-icons>
						<text class="card-actions-item-text">点赞</text>
					</view>
					<view class="card-actions-item" @click="actionsClick('comment')">
						<uni-icons type="chatbubble" size="18" color="#999"></uni-icons>
						<text class="card-actions-item-text">评论</text>
					</view>
				</view>
			</uni-card>
			<uni-section title="卡片+列表" type="line">
				<uni-card padding="0" spacing="0">
					<template v-slot:cover>
						<view class="custom-cover">
							<image class="cover-image" mode="aspectFill" :src="cover2">
							</image>
							<view class="cover-content">
								<text class="uni-subtitle uni-white">今日新闻热点</text>
							</view>
						</view>
					</template>
					<uni-list>
						<uni-list-item title="今日新闻" showArrow></uni-list-item>
						<uni-list-item title="今日新闻" showArrow></uni-list-item>
					</uni-list>
					<view slot="actions" class="card-actions no-border">
						<view class="card-actions-item" @click="actionsClick('分享')">
							<uni-icons type="pengyouquan" size="18" color="#999"></uni-icons>
							<text class="card-actions-item-text">分享</text>
						</view>
						<view class="card-actions-item" @click="actionsClick('点赞')">
							<uni-icons type="heart" size="18" color="#999"></uni-icons>
							<text class="card-actions-item-text">点赞</text>
						</view>
						<view class="card-actions-item" @click="actionsClick('评论')">
							<uni-icons type="chatbubble" size="18" color="#999"></uni-icons>
							<text class="card-actions-item-text">评论</text>
						</view>
					</view>
				</uni-card>
			</uni-section>
			<uni-popup ref="popup" type="bottom">
				<uni-list>
					<uni-list-item title="列表文字" note="列表描述信息"></uni-list-item>
					<uni-list-item :disabled="true" title="列表文字" note="列表禁用状态"></uni-list-item>
				</uni-list>
			</uni-popup>
		</uni-section>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				href: 'https://uniapp.dcloud.io/component/README?id=uniui',
				cover: 'http://p1.music.126.net/i-WNw8_TConqML8O3GSFdw==/109951167767753233.jpg',
				cover2: 'http://p1.music.126.net/eEYKjzeVdeiDXsFKdkkXSQ==/109951167767767196.jpg',
				avatar: 'https://p2.music.126.net/cjh_BIDWLqk7c0Ytiwakqw==/18961078021601966.jpg'
			}
		},
		created() {
			this.init()
		},
		methods: {
			async init() {
				uni.setClipboardData({
					data: 'hello',
					complete: function() {
						console.log('complete');
					}
				})
				console.log(new Date().getTime())
				await this.test()
				uni.getClipboardData({
					complete: result => {
						console.log('result => ', result)
					}
				})
				console.log(new Date().getTime())
			},
			test() {
				return new Promise((res, rej) => {
					setTimeout(() => {
						res(0)
					}, 400)
				})
			},
			actionsClick(type) {
				console.log('type', type)
				type === 'share' && (this.$refs.popup.open())
			},
		}
	}
</script>

<style>
	.container {
		padding: 20px;
		font-size: 14px;
		line-height: 24px;
	}
</style>
