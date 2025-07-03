<template>
	<view class="content">
		<back ref="child" :text="myAddress" type="1" @getMsg="getMsg"></back>
		<view class="scorView">
			<swiper class="swiper" circular :indicator-dots="indicatorDots" indicator-color="#fff" indicator-active-color="#E49E08" :autoplay="autoplay" :interval="interval"
				:duration="duration">
				<swiper-item class="swiper-item"> 
					<image src="/static/swiper.png" mode=""></image>
				</swiper-item>
			<!-- 	<swiper-item class="swiper-item" v-if="langType==0">
					<image src="/static/bgIndex1.jpg" mode=""></image>
				</swiper-item>
				<swiper-item class="swiper-item" v-else>
					<image src="/static/bgIndex2.jpg" mode=""></image>
				</swiper-item> -->
				<swiper-item class="swiper-item" v-if="langType==0">
					<image src="/static/bgIndex4.jpg" mode=""></image>
				</swiper-item>
				<swiper-item class="swiper-item" v-else>
					<image src="/static/bgIndex3.jpg" mode=""></image>
				</swiper-item>
			</swiper>
		</view>
		<view class="bulletin">
			<view class="bulImg">
				<image src="/static/bulletin.png" mode=""></image>
			</view>
			<view class="text">
				0xB8549a……5B17B mint1000TH/s
			</view>
		</view>
		
		<view class="boxView">
			<view class="title">
				{{$t('index1')}}
			</view>
			<view class="hashrate">
				<view class="num">
					{{allPower}}TH/s
				</view>
				<view class="text">
					{{$t('index2')}}
				</view>
			</view>
			<view class="btn" @click="copy">
				{{$t('home9')}}
			</view>
		</view>
		<view class="about">
			<view class="title">
				<view class="line"></view>
				<view class="text">
					{{$t('index4')}}
				</view>
			</view>
			<view class="img1">
				<image src="/static/img1.png" mode=""></image>
			</view>
			<view class="img2">
				<image src="/static/img2.png" mode=""></image>
			</view>
		</view>
		
		<view class="customer">
			<view class="title">
				<view class="text">
					{{$t('index5')}}
				</view>
				<view class="text1">
					{{$t('index6')}}
				</view>
			</view>
			<view class="info">
				<view class="samll1">
					{{$t('index7')}}
				</view>
				<view class="list">
					<view class="item">
						<view class="text">
							{{$t('index8')}}
						</view>
					</view>
					<view class="item">
						<view class="text">
							{{$t('index9')}}
						</view>
					</view>
					<view class="item">
						<view class="text">
							{{$t('index10')}}
						</view>
					</view>
				</view>
				<view class="list">
					<view class="item">
						<view class="text">
							{{$t('index11')}}
						</view>
					</view>
					<view class="item">
						<view class="text">
							{{$t('index12')}}
						</view>
					</view>
				</view>
			</view>
		</view>
		
		<view class="watch about">
			<view class="title">
				<view class="line"></view>
				<view class="text">
					{{$t('index13')}}
				</view>
			</view>
			<view class="videoInfo">
				<video class="info" id="myVideo" src="/static/video.mp4"
				    @error="videoErrorCallback" enable-danmu controls></video>
			</view>
		</view>
		
		<view class="watch about application" :class="langType!=0?'application1':''">
			<view class="title">
				<view class="line"></view>
				<view class="text">
					{{$t('index14')}}
				</view>
			</view>
			<view class="NavInfo">
				<view class="list">
					<view class="item">
						<view class="img">
							<image src="/static/listNav1.png"></image>
						</view>
						<view class="title">
							<view class="info">
								{{$t('index15')}}
							</view>
						</view>
						<view class="samll">
							{{$t('index19')}}
						</view>
					</view>
					<view class="item">
						<view class="img">
							<image src="/static/listNav2.png"></image>
						</view>
						<view class="title">
							<view class="info">
								{{$t('index16')}}
							</view>
						</view>
						<view class="samll">
							{{$t('index20')}}
						</view>
					</view>
					<view class="item">
						<view class="img">
							<image src="/static/listNav3.png"></image>
						</view>
						<view class="title">
							<view class="info">
								{{$t('index17')}}
							</view>
						</view>
						<view class="samll">
							{{$t('index21')}}
						</view>
					</view>
					<view class="item">
						<view class="img">
							<image src="/static/listNav4.png"></image>
						</view>
						<view class="title">
							<view class="info">
								{{$t('index18')}}
							</view>
						</view>
						<view class="samll">
							{{$t('index22')}}
						</view>
					</view>
				</view>
			</view>
		</view>
		<view class="watch about smart" :class="langType!=0?'smart1':''">
			<view class="title">
				<view class="line"></view>
				<view class="text">
					{{$t('index23')}}
				</view>
			</view>
			<view class="NavInfo">
				<view class="list" :class="langType!=0?'enNavInfo':''">
					<view class="item">
						<view class="img">
							<image src="/static/smart1.png"></image>
						</view>
						<view class="samll">
							{{$t('index24')}}
						</view>
					</view>
					<view class="item">
						<view class="img">
							<image src="/static/smart2.png"></image>
						</view>
						<view class="samll">
							{{$t('index25')}}
						</view>
					</view>
					<view class="item">
						<view class="img">
							<image src="/static/smart3.png"></image>
						</view>
						<view class="samll">
							{{$t('index26')}}
						</view>
					</view>
				</view>
			</view>
		</view>
		<view class="seat"></view>
		<uni-popup ref="popup" type="center" :mask-click="false">
			<view class="insureBox">
				<view class="titlePup">
					<view class="pupBox">
						<view class="name">
							{{$t('home26')}}
						</view>
					</view>
				</view>
				<view class="inputPup">
					<input placeholder-style="color:#666" :placeholder="$t('home27')" type="text" v-model="userAddress" disabled>
				</view>
				<view class="btnPup" @click="clickBind()">
					<view class="text">
						{{$t('home28')}}
					</view>
				</view>
			</view>
		</uni-popup>
		<w-loading text="" mask="true" click="false" ref="loading"></w-loading>
		<uv-picker ref="picker" :confirmText="$t('home28')" :cancelText="$t('home31')" :columns="columns" @confirm="changeIdo"></uv-picker>
	</view>
</template>

<script>
	import swal from 'sweetalert';
	import back from "@/component/back/index.vue";
	import abi from "../../abi/abi.json";
	import bignumberJS from "bignumber.js"
	import {allowance,usdtApprove,mobileFilter,usdtMoney} from "../../abi/ft.js"
	import wLoading from "@/component/w-loading/w-loading.vue";
	import {getMyInfo,getSystem} from "@/abi/userMG1.js"
	var nowTimer;
	var adressMain="0x6232cBB2D34be1BD5DE05953eBAa65E63D48Dc86"
	export default {
		components:{
			wLoading,back
		},
		data() {
			return {
				columns: [['1000', '3000', '10000', '50000']],
				myAddress: '',
				isTopBind:'',
				userAddress: '',
				userAddress1:'',
				userAddress2:'',
				Approve:false,
				allowanceB:0,
				tabList: ['home19','home20'],
				tapIndex: 0,
				drawalAmount:'',
				allPower:'',
				myPower:'',
				grade:'',
				myDrawalAmount:'',
				deliverAddress:'',
				activeType:"",
				activeNum:"",
				teamLevel:'',
				maxTeam:'',
				minTeam:'',
				indicatorDots: true,
				autoplay: true,
				interval: 2000,
				duration: 500,
				langType:1
			}
		},
		filters: {
			plusXing2(str) {
				if (str.length == 0) {
					return "";
				}
				var len = str.length - 4;
				var xing = '';
				for (var i = 0; i < 4; i++) {
					xing += '*';
				}
				return str.substring(0, 4) + xing + str.substring(str.length - 4);
			}
		},
		onLoad(option) {
			this.langType=uni.getStorageSync("indexVal");
			this.userAddress = option.userAddress == undefined ? '' : option.userAddress;
			let _this = this;
			_this.Init(() => {
				uni.setStorageSync("address", this.myAddress);
				let provider = new _this.ethers.providers.Web3Provider(window.ethereum);
				_this.contract = new _this.ethers.Contract(_this.contractAddress, abi, provider.getSigner());
				// _this.urlStr='https://www.arbsdapp.com/#/?userAddress='+_this.myAddress;
				// _this.getCalInfo();
				_this.bindTop();
				_this.getMyInfo()
				_this.getNeedUActive();
				
				_this.Fallowance();
				_this.getSystem();
			});
		},
		methods: {
			scroll(e) {
				console.log(e)
			},
			getSystem(){
				getSystem().then(res => {
					if (res.code == 0) {
						let num=res.data[0].allCal;
						if(parseInt(num) === parseFloat(num)){
							this.allPower=parseInt(num);
						}else{
							this.allPower=Number(num).toFixed(4);
						}
					}
				});
			},
			getMyInfo(){
				getMyInfo({"address":this.myAddress}).then(res => {
				if (res.code == 0) {
					if(res.data.length>0){
						this.teamLevel=res.data[0].teamLevel;
						this.maxTeam=res.data[0].maxTeam;
						this.minTeam=res.data[0].minTeam;
						this.myPower=res.data[0].myScore;
						this.isTopBind = res.data[0].bindAddress;
						if (this.isTopBind == null && this.myAddress.toLowerCase() != adressMain.toLowerCase()) {
							this.$refs.popup.open();
						}else if(this.isTopBind.length < 10){
							this.$refs.popup.open();
						}
					}else{
						let bindSync=uni.getStorageSync('bindAddress');
						if(bindSync=='0x0000000000000000000000000000000000000000' && this.myAddress.toLowerCase() != adressMain.toLowerCase()){
							this.$refs.popup.open();
						}
						// uni.setStorageSync("bindAddress", '0x0000000000000000000000000000000000000000');
					}
				}
				});
			},
			// methods: {getNeedUActive 获取能否激活每月算力,
			async getNeedUActive(){
				this.contract.getNeedUActive(this.myAddress).then((res, err) => {
					this.activeType=res[0];
					this.activeNum=mobileFilter(res[1]);
				});
			},
			async setGiveAdult(){
				this.$refs.loading.open();
				let res=await this.contract.giveAdult(this.userAddress2).catch(err=>{
					this.$refs.loading.close();
					let errJson = JSON.parse(JSON.stringify(err));
					swal({
						title: this.$t('fromData13'),
						text: errJson.reason,
						icon: "error",
					})
				})
				if(res){
					await res.wait();
					this.$refs.loading.close();
					swal({
						title: this.$t('success'),
						icon: "success",
					})
				}
			},
			
			async changeIdo(e){
				this.$refs.loading.open();
				let res=await this.contract.IDO(e.indexs[0]).catch(err=>{
					this.$refs.loading.close();
					let errJson = JSON.parse(JSON.stringify(err));
					swal({
						title: this.$t('fromData13'),
						text: errJson.reason,
						icon: "error",
					})
				})
				if(res){
					await res.wait();
					this.$refs.loading.close();
					swal({
						title: this.$t('success'),
						icon: "success",
					})
				}
			},
			copy() {
				let _this = this;
				if(_this.isTopBind == '0x0000000000000000000000000000000000000000'){
					uni.showToast({
						icon: 'none',
					    title: this.$t('log6')
					});
					return
				}
				uni.setClipboardData({
					data: 'https://www.b2-dpo.life/#/?userAddress='+this.myAddress,
					success: function () {
						swal({
							title: _this.$t('success'),
							text: _this.$t('new2'),
							icon: "success",
						})
					}
				});
			},
			plusXing2(str) {
				// console.log(str)
				if (str.length == 0) {
					return "";
				}
				if (str == '0x0000000000000000000000000000000000000000'&& str.toLowerCase() != this.userAddress.toLowerCase()) {
					return this.$t('fromData12')
				}
				var len = str.length - 4;
				var xing = '';
				for (var i = 0; i < 3; i++) {
					xing += '*';
				}
				return str.substring(0, 4) + xing + str.substring(str.length - 5);
			},
			clickTap(val) {
				this.tapIndex = val;
			},
			clickBing() {
				this.$refs.popup1.open();
			},
			getMsg(e){
				console.log(e);
				this.langType=e;
			},
			bindTop() {
				this.contract.getParent(this.myAddress).then((res, err) => {
					this.isTopBind = res;
					uni.setStorageSync("bindAddress", res);
				});
			},
			mobileFilter1(val){
				let inNumber = val.toString();
				return inNumber
			},
			mobileFilter2(val){
				let inNumber = val.toString();
				let num=this.ethers.utils.formatUnits(inNumber);
				if(parseInt(num) === parseFloat(num)){
					return parseInt(num)
				}else{
					return Number(num).toFixed(4)
				}
			},
			Fallowance(){
				allowance(this.myAddress,this.contractAddress).then(res=>{
					if(res){
						let amount=mobileFilter(res);
						this.allowanceB=amount;
						console.log(parseInt(amount));
						if(parseInt(amount)<= parseInt(0)){
							this.Approve=false;
						}else{
							this.Approve=true;
						}
					}
				})
			},
			// 授权
			async FApprove(){
				this.$refs.loading.open();
				let res=await usdtApprove(this.contractAddress).catch(err=>{
					this.$refs.loading.close();
					let errJson = JSON.parse(JSON.stringify(err));
					swal({
						title: "失败",
						text: errJson.reason,
						icon: "error",
					})
				})
				if(res){
					await res.wait();
					this.$refs.loading.close();
					this.Fallowance();
					swal({
						title: this.$t('success'),
						icon: "success",
					})
				}else{
					this.$refs.loading.close();
				}
				
			},
			async clickBind() {
				this.$refs.loading.open();
				let res = await this.contract.bindParent(this.userAddress).catch(err => {
					this.$refs.loading.close();
					let errJson = JSON.parse(JSON.stringify(err));
					uni.showToast({
						title: errJson.reason,
						icon: "none"
					})
				});
				if (res) {
					try {
						await res.wait();
						this.$refs.loading.close();
						uni.showToast({
							title: this.$t('success'),
							icon: "none"
						})
						this.bindTop();
						this.$refs.popup.close();
					} catch (e) {
						console.log(e);
						this.$refs.loading.close();
						this.$refs.popup.close();
						uni.showToast({
							title: e.toString(),
							icon: "none"
						})
					}
				}
			},
			async Init(callback) {
				if (typeof window.ethereum === "undefined") {
					console.log("请安装MetaMask")
				} else {
					let wert = new this.ethers.providers.Web3Provider(window.ethereum);
					const accounts = await wert.send("eth_requestAccounts", []);
					await window.ethereum.request({ method: 'eth_requestAccounts' });
					this.myAddress = accounts[0];
					callback();
				}
			}
		}
	}
</script>

<style lang="less" scoped>
	.seat{
		background-color: #000;
		height: 20upx;
	}
	.content {
		width: 100%;
		height: 100%;
		background-color: #100F0B;
		background-size: 100% 100%;
		min-height: 100vh;
		box-sizing: border-box;
		// padding: 0 30rpx 10rpx 30rpx;
		.bulletin{
			margin: 20upx 40upx 0;
			height: 101upx;
			background: #191917;
			border-radius: 20upx 20upx 20upx 20upx;
			border: 2upx solid #403C34;
			display: flex;
			align-items: center;
			padding: 0 29upx;
			.bulImg{
				width: 38upx;
				height: 34upx;
				margin-right: 20upx;
				image{
					width: 100%;
					height: 100%;
				}
			}
			.text{
				font-size: 26upx;
				color: #FFFFFF;
			}
		}
		.boxView{
			margin: 20upx 40upx 0;
			background: #191917;
			border-radius: 20upx 20upx 20upx 20upx;
			border: 2upx solid;
			border-image: radial-gradient(circle, rgba(192, 166, 128, 1), rgba(16, 15, 11, 1)) 1 1 0 1;
			padding: 30upx;
			.title{
				text-align: center;
				font-size: 28upx;
				color: #FFFFFF;
			}
			.hashrate{
				margin-top: 30upx;
				background: #191917;
				border-radius: 25upx 25upx 25upx 25upx;
				border: 2upx solid #403C34;
				padding: 30upx;
				.num{
					font-size: 48upx;
					color: #DCB685;
					text-align: center;
				}
				.text{
					font-size: 28upx;
					color: #DCB685;
					text-align: center;
					margin-top: 10upx;
				}
			}
			.btn{
				margin-top: 25upx;
				background: linear-gradient(to right, #E9CC9E 30%, #D5AB78 70%);
				border-radius: 43upx;
				text-align: center;
				padding: 25upx;
			}
		}
		.about{
			margin-top: 40upx;
			height: 395upx;
			background-image: url('/static/indexBg1.png');
			background-size: 100% 100%;
			padding: 0 40upx;
			// background-color: #100F0B;
			.title{
				display: flex;
				align-items: center;
				.line{
					width: 5upx;
					height: 29upx;
					background-color: #D5AB78;
					border-radius: 20upx;
					margin-right: 15upx;
				}
				.text{
					font-size: 34upx;
					color: #FFFFFF;
				}
			}
			.img1{
				position: absolute;
				bottom: -40upx;
				width: 96upx;
				height: 111upx;
				left: 40upx;
				image{
					width: 96upx;
					height: 111upx;
				}
			}
			.img2{
				width: 41upx;
				height: 27upx;
				position: absolute;
				bottom: -40upx;
				left: 0;
				right: 0;
				margin: 0 auto;
				image{
					width: 41upx;
					height: 27upx;
				}
			}
		}
		.customer{
			margin: 20upx 40upx 0;
			.title{
				text-align: center;
				.text{
					font-weight: 900;
					font-size: 32upx;
					color: #FFFFFF;
				}
				.text1{
					margin-top: 10upx;
					font-size: 26upx;
					color: #FFFFFF;
				}
			}
			.info{
				margin-top: 20upx;
				background: linear-gradient(to right, #272727 30%, #2F261E 70%);
				border-radius: 15upx;
				padding: 33upx 27upx;
				.samll1{
					font-size: 24upx;
					color: #FFFFFF;
					margin-bottom: 20upx;
				}
				.list{
					display: flex;
					align-items: center;
					justify-content: space-between;
					margin-bottom: 20upx;
					.item{
						background: #292725;
						border-radius: 30upx;
						border: 2upx solid #403C34;
						padding: 15upx 20upx;
						.text{
							padding: 0 10upx;
							font-size: 24upx;
							color: #FFFFFF;
						}
					}
				}
			}
		}
		.application{
			.NavInfo{
				.list{
					display: flex;
					align-items: center;
					flex-wrap: wrap;
					justify-content: space-between;
					box-sizing: border-box;
					.item{
						box-sizing: border-box;
						width: 48%;
						height: 380upx;
						background: #191917;
						border-radius: 20upx;
						margin: 10upx 0;
						.img{
							width: 65upx;
							height: 65upx;
							margin: 33upx auto 0;
							image{
								width: 100%;
								height: 100%;
							}
						}
						.title{
							height: 107upx;
							margin: 10upx 30upx 0;
							.info{
								margin: 0 auto;
								font-size: 30upx;
								color: #DCB685;
							}
						}
						.samll{
							text-align: center;
							margin: 20upx 10upx 0;
							font-size: 24upx;
							color: #FFFFFF;
						}
					}
				}
			}
		}
		.application1{
			.NavInfo{
				.list{
					display: flex;
					align-items: center;
					flex-wrap: wrap;
					justify-content: space-between;
					box-sizing: border-box;
					.item{
						box-sizing: border-box;
						width: 48%;
						height: 450upx;
						background: #191917;
						border-radius: 20upx;
						margin: 10upx 0;
						.img{
							width: 65upx;
							height: 65upx;
							margin: 33upx auto 0;
							image{
								width: 100%;
								height: 100%;
							}
						}
						.title{
							height: 107upx;
							margin: 10upx 30upx 0;
							.info{
								margin: 0 auto;
								font-size: 30upx;
								color: #DCB685;
							}
						}
						.samll{
							text-align: center;
							margin: 20upx 10upx 0;
							font-size: 24upx;
							color: #FFFFFF;
						}
					}
				}
			}
		}
		.smart{
			.NavInfo{
				.list{
					display: flex;
					align-items: center;
					flex-wrap: wrap;
					justify-content: space-between;
					box-sizing: border-box;
					.item{
						box-sizing: border-box;
						width: 32%;
						// height: 450upx;
						padding-bottom: 30upx;
						background: #191917;
						border-radius: 20upx;
						margin: 10upx 0;
						.img{
							width: 58upx;
							height: 52upx;
							margin: 33upx auto 0;
							image{
								width: 100%;
								height: 100%;
							}
						}
						.samll{
							text-align: center;
							margin: 20upx 15upx 0;
							font-size: 24upx;
							color: #FFFFFF;
						}
					}
				}
				.enNavInfo{
					.item{
						height: 450upx;
						padding-bottom: 0;
					}
				}
			}
		}
		.watch{
			background-color: #000;
			background-image: none;
			height: auto;
			.videoInfo{
				margin-top: 20upx;
				height: 370upx;
				.info{
					width: 100%;
					height: 370upx;
				}
			}
		}
		.dpoMain{
			margin: 0 40upx;
			background: rgba(0, 0, 0, 0.5);
			padding: 30upx;
			box-sizing: border-box;
			position: fixed;
			border-radius: 15upx;
			bottom: 109upx;
			left: 0;
			right: 0;
			.title{
				display: flex;
				align-items: center;
				.img{
					width: 48upx;
					height: 49upx;
					margin-right: 19upx;
					image{
						width: 100%;
						height: 100%;
					}
				}
				.version{
					display: flex;
					align-items: center;
					.text{
						font-size: 28upx;
						color: #D48800;
						margin-right: 19upx;
					}
					.samll{
						font-size: 28upx;
						color: #FDC314;
					}
				}
			}
			.DataList{
				margin-top: 61upx;
				border: 2upx solid;
				padding: 40upx 30upx;
				border-color: rgba(228, 158, 8, 0.5);
				border-radius: 10upx;
				.item{
					display: flex;
					align-items: center;
					justify-content: space-between;
					margin-bottom: 25upx;
					.text{
						font-family: MicrosoftYaHeiLight;
						font-size: 32upx;
						color: #D48800;
					}
					.num{
						font-family: MicrosoftYaHei;
						font-size: 32upx;
						color: #FDC314;
					}
				}
				.item:last-child{
					margin-bottom: 0;
				}
			}
			.operateBtn{
				display: flex;
				align-items: center;
				justify-content: space-between;
				margin: 50upx 0upx 0;
				.item{
					width: 184upx;
					height: 91upx;
					background: rgba(228, 158, 8, 0.1);
					border-radius: 10upx;
					border: 2upx solid;
					border-color: rgba(228, 158, 8, 0.5);
					// opacity: 0.6;
					display: flex;
					align-items: center;
					justify-content: center;
					.img{
						width: 30upx;
						height: 30upx;
						margin-right: 15upx;
						image{
							width: 100%;
							height: 100%;
						}
					}
					.text{
						font-family: MicrosoftYaHei;
						font-size: 28upx;
						color: #FDC314;
					}
				}
			}
		}
	}
	.insureBox{
		width: 650upx;
		box-sizing: border-box;
		border-radius: 15upx;
		border: 2upx solid;
		background-color: #1B1B19;
		padding: 40upx 30upx;
		position: relative;
		.colse{
			position: absolute;
			right: 30upx;
			width: 35upx;
			height: 35upx;
			image{
				width: 100%;
				height: 100%;
			}
		}
		.titlePup{
			.pupBox{
				text-align: center;
				.logo{
					width: 75upx;
					height: 77upx;
					margin-bottom: 20upx;
					image{
						width: 100%;
						height: 100%;
					}
				}
				.name{
					color: #fff;
				}
			}
		}
		.inputPup{
			border: 2upx solid;
			border-color: #333335;
			padding: 30upx 15upx;
			border-radius: 25upx;
			margin-top: 30upx;
			color: #fff;
		}
		.btnPup{
			height: 100upx;
			border-radius: 25upx;
			background: linear-gradient(to right, #E9CC9E 30%, #D5AB78 70%);
			display: flex;
			align-items: center;
			justify-content: center;
			margin: 30upx auto 0;
			.text{
				font-family: MicrosoftYaHei;
				font-size: 34upx;
				color: #100F0B;
			}
		}
	}
	.idoBtn{
		position: fixed;
		border-radius: 15upx;
		bottom: 50upx;
		left: 0;
		right: 0;
		margin: 0 auto;
		width: 184upx;
		height: 91upx;
		background: rgba(228, 158, 8, 0.1);
		border-radius: 10upx;
		border: 2upx solid;
		border-color: rgba(228, 158, 8, 0.5);
		// opacity: 0.6;
		display: flex;
		align-items: center;
		justify-content: center;
		.text{
			font-family: MicrosoftYaHei;
			font-size: 28upx;
			color: #FDC314;
		}
	}
	.tipText{
		text-align: center;
		color: #fff;
		margin-top: 15upx;
	}
	.scorView{
		width: 90%;
		margin: 0 auto;
		height: 300upx;
		border-radius: 20upx;
		margin-top: 20upx;
		.swiper{
			.swiper-item{
				border-radius: 20upx;
				image{
					width: 100%;
					border-radius: 20upx;
					height: 100%;
				}
			}
			
		}
	}
</style>
