
<template>
	<div class="main-body">
    <News />
		<div class="template">
			<div class="container">
				<div class="row flex">
					<div class="banner-image col-md-9 col-xs-12">
						<img src="https://image-cdn.hypb.st/https%3A%2F%2Fhbx.hypebeast.com%2Ffiles%2F2020%2F10%2Fwe11done-gdragon-womens-mens-fashion-clothing-winter-suits-blazers-16.jpg?q=90&w=1600&fit=max&v=1" />
					</div>
					<div class="banner-body col-md-3 col-xs-12">
						<div class="banner-txt">
							<h2>新到貨品</h2>
							<p>最新秋冬2020系列服饰</p>
							<a>选购男装</a>
							<a>选购女装</a>
						</div>
					</div>
				</div>
			</div>
		</div>
	    <div class="template">
			<div class="container">
				<div class="row" >
<!--					<div class="col-md-6 col-xs-12">-->
<!--						<img src="https://image-cdn.hypb.st/https%3A%2F%2Fhbx.hypebeast.com%2Ffiles%2F2020%2F09%2Fhyein-seo-hp-banner.jpg?q=90&w=800&fit=max&v=1">-->
<!--						<div class="banner-txt2">-->
<!--							<h3>最新发售</h3>-->
<!--							<h2>HYEIN SEO</h2>-->
<!--							<p>最新产品带有品牌标志性的战术服装和配饰。</p>-->
<!--							<a>选购男装</a>-->
<!--							<a>选购女装</a>-->
<!--						</div>-->
<!--					</div>-->
					<div class="col-md-6 col-xs-12"  v-for="(item,index) in homeCloses" :key="index">
						<img :src="item.img" >
					    <div class="banner-txt2">
					    	<h3>{{item.title}}</h3>
					    	<h2>{{item.name}}</h2>
					    	<p>{{item.describ}}</p>
					    	<a style="margin-left: 0;">立即选购</a>
					    </div>
					</div>
				</div>
			</div>
		</div>
<!--	    <div class="template">-->
<!--	    	<div class="container">-->
<!--	    		<div class="row flex">-->
<!--					-->
<!--	    			<div class="banner-image col-md-9 col-xs-12 col-md-push-3">-->
<!--	    				<img src="https://image-cdn.hypb.st/https%3A%2F%2Fhbx.hypebeast.com%2Ffiles%2F2020%2F10%2Fhypebae-reebok-campaign-oct8-1600x900-option1.jpg?q=90&w=1600&fit=max&v=1" />-->
<!--	    			</div>-->
<!--	    			<div class="banner-body col-md-3 col-xs-12 col-md-pull-9">-->
<!--	    				<div class="banner-txt2">-->
<!--	    					<h3>限量發售</h3>-->
<!--	    					<h2>HYPEBAE x Reebok DMX Thrill</h2>-->
<!--	    					<p>破格中性设计的联乘波鞋款式</p>-->
<!--	    					<a style="margin-left: 0;">立即选购</a>-->
<!--	    				</div>-->
<!--	    			</div>-->
<!--	    		</div>-->
<!--	    	</div>-->
<!--	    </div>-->
<!--	    <div class="template">-->
<!--	    	<div class="container">-->
<!--	    		<div class="row">-->
<!--&lt;!&ndash;	    			<div class="col-md-6 col-xs-12">&ndash;&gt;-->
<!--&lt;!&ndash;	    				<img src="https://image-cdn.hypb.st/https%3A%2F%2Fhbx.hypebeast.com%2Ffiles%2F2020%2F10%2Fwomens-fashion-clothing-coats-jackets-fw20-ader-error-ance-studios-fw20-12.jpg?q=90&w=800&fit=max&v=1">&ndash;&gt;-->
<!--&lt;!&ndash;	    				<div class="banner-txt2">&ndash;&gt;-->
<!--&lt;!&ndash;	    					<h3>配搭必備</h3>&ndash;&gt;-->
<!--&lt;!&ndash;	    					<h2>秋冬精選</h2>&ndash;&gt;-->
<!--&lt;!&ndash;	    					<p>包括最熱門款式</p>&ndash;&gt;-->
<!--&lt;!&ndash;	    					<a style="margin-left: 0;">立刻选购</a>&ndash;&gt;-->
<!--&lt;!&ndash;	    				</div>&ndash;&gt;-->
<!--&lt;!&ndash;	    			</div>&ndash;&gt;-->
<!--	    			<div class="col-md-6 col-xs-12">-->
<!--	    				<img src="https://image-cdn.hypb.st/https%3A%2F%2Fhbx.hypebeast.com%2Ffiles%2F2020%2F10%2Fbag-womens-fashion-bottega-veneta-loewe-marine-serre-acne-studios-chloe-fw20-12.jpg?q=90&w=800&fit=max&v=1">-->
<!--	    			    <div class="banner-txt2">-->
<!--	    			    	<h3>新品上架</h3>-->
<!--	    			    	<h2>精选手袋</h2>-->
<!--	    			    	<p>最热门款式包括品牌 LOEWE, BURBERRY, Bottega Veneta, Alexander Wang。</p>-->
<!--	    			    	<a style="margin-left: 0;">立刻选购</a>-->
<!--	    			    </div>-->
<!--	    			</div>-->
<!--	    		</div>-->
<!--	    	</div>-->
<!--	    </div>-->
	    <Brand />
	</div>
</template>

<script>
import Brand from '../brands/brand'
import {getHomeMultData} from '../../network/home'
import News from "../../components/news"
	export default {
    name: "Home",
    components:{
      Brand,
      News
    },
    created() {
    	this.loadData();
	},
	data(){
    	return{
           homeCloses:[]
		}
	},
    methods:{
    	loadData(){
    		getHomeMultData().then(res =>{
    			this.homeCloses =  res.data.homecloses;
			}).catch(error=>{

			})
		}
	}
	}
</script>

<style scoped>
	.template{
		margin: 15px;
	}
	.banner-txt h2,p,a{
		font-weight: 700;
	}
	.banner-txt h2{
		font-size: .35rem;
	}
    .banner-txt p{
		font-size: .16rem;
	}
	.banner-txt a{
		color: #000000;
		cursor: pointer;
		font-size: .16rem;
		line-height: .4rem;
	}
	.banner-txt a:last-child{
		margin-left: 10px;
	}
	.container img {
		width: 100%;
	}

	@media (min-width: 992px) {
		.container {
			width: 1250px !important;
		}
		.flex {
			display: flex;
			align-items: flex-end;
		}
	}
	/* 组件2样式 */
	.banner-txt2{
		margin: 0.2rem 0;
	}
	.banner-txt2 h2,p,a{
		font-weight: 700;
	}
	.banner-txt2 h2{
		font-size: .32rem;
		margin-top: 10px;
	}
	.banner-txt2 h3{
		font-size: .14rem;
		font-weight: 400;
	}
	.banner-txt2 p{
		font-size: 16px;
	}
	.banner-txt2 a{
		color: #000000;
		cursor: pointer;
		font-size: .16rem;
	}
	.banner-txt2 a:last-child{
		margin-left: .16rem;
	}
</style>

