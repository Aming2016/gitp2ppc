<template>
	<div class="investonehomebox">
			<div class="boxswiperdiv" v-show="showone"> 
  				<div id="boxswiperdivone">平台成交金额</div>
  				<div id="boxswiperdivtwo">{{data.total_amount}}<span>元</span></div>
  				<div id="boxswiperdivthree">第三方资金托管</div>
  				<div id="boxswiperdivfour">轻松投资 | 乐享收益</div>
  				<router-link tag="button" to="/logname" class="btn btnone">注册立享1000.00元好礼</router-link>

  				<router-link tag="div" to="/register" id="boxswiperdivfive">
  					<span>立即登录</span>
  					<img src="../../imgs/home/lijideng.png"/>
  				</router-link>
 			</div>
		
		<div class="swiper-container swipercontent">
			<div class="swiper-wrapper">
					<div  class="swiper-slide swipersdiv" v-for="item in data.banner_list_pc">						
					<a :href="item.content_url"  target="_blank"><img :src="imgurl+item.url"/></a>
					</div>
				
			</div>
					    <!-- 如果需要分页器 -->
			<div class="swiper-pagination"></div>
					    
					    <!-- 如果需要导航按钮 -->
			<div class="swiper-button-prev"></div>
			<div class="swiper-button-next"></div>
		</div>
		<div class="homeulonebox">
			<ul id="homeulone">
				<li>
					<div>平台用户</div>
					<div>{{data.total_member}}<span>人</span></div>
				</li>
				<li>
					<div>累计投资金额</div>
					<div>{{data.total_amount}}<span>元</span></div>
				</li>
				<li>
					<div>已发放收益</div>
					<div>{{data.total_interest}}<span>元</span></div>
				</li>
			</ul>
			
		</div>
		
	<div class="investonehome">
		<ul id="homeultwo">
			<li>
				<div>
					<div>
						<img src="../../imgs/home/shouyis.png"/>
					</div>
					<div>
						<div>收益稳定</div><br />
						<div>100元起投，高于银行倍数的年化利率，足不出户即可稳赚收益</div>
					</div>
					
				</div>
			</li>
			<li>
				<div>
					<div>
						<img src="../../imgs/home/fangchans.png"/>
					</div>
					<div>
						<div>房产供应链金融</div><br />
						<div>房产解押，贷款过桥，房产抵押借款，不良房地产资产快速流转</div>
					</div>
					 
				</div>
			</li>
			<li>
				<div>
					<div>
						<img src="../../imgs/home/fengkongs.png"/>
					</div>
					<div>
						<div>风控机制</div><br />
						<div>房产信息全掌控，抵押备案为依托，全面杜绝不良风险</div>
					</div>
					
				</div>				
			</li>
		</ul>
		<div id="homedivone" v-if="tybprojectlist.length!='0'">
			<div style="border-bottom:1px solid #cacaca;">
				<span>新手专享</span>
				<router-link  tag="span" to="/helpcenone">新手指引</router-link>
				<p @click="investonehomebtn"><span>更多</span><img src="../../imgs/home/jiantouyi.png"/></p>
			</div>
			<ul class="ul_1">
				<li class="li_1" v-for="item in tybprojectlist">
					<div>
						<div>
							<p>{{item.display_rate}}% <span v-show="item.label_str!=''">{{item.label_str}}</span></p>
							<p>预计年化利率</p>
						</div>
						<div>
							<p>{{item.issue_count}}</p>
							<p>期限</p>
						</div>
						<div>
							<p>{{item.repay_type_display}}</p>
							<p>还款方式</p>
						</div>
						<div>
							<p>{{item.min_amount}}元</p>
							<p>起投金额</p>
						</div>
						<div>
							<p>{{item.amount}}元</p>
							<p>借款总额</p>
						</div>
						<div @click="gobtn(item)">
							立即投资
						</div>
					</div>
				</li>
			</ul>
		</div>
		<div class="homedivtwo">
			<div>
				<span>标预告</span>
				<router-link tag="div" to="/investonehome" style="cursor: pointer;margin-right:20px;">
					投资抢先一步
				</router-link>
			</div>
			<div>
				<div id="imgidv">
					<img src="../../imgs/home/homeimgthree.png"/>
				</div>
				
				
				<div class="swiper-containers" id="hk_btextbox">
				  <div class="swiper-wrapper">
				  	<div class="swiper-slide swiperwarp" v-for="(item,index) in foreshowlist">				  	
				    <div class=" swepersbox">
							<div class="biaoqianid" v-show="item.label_str!=''">
								<span>{{item.label_str}}</span>
							</div>
							<div id="hk_text1">
								<div>{{item.project_type_display}}</div>
								<div v-show="item.is_lock">锁</div>
							</div>
							<div id="hk_text2">
								{{item.name}}
							</div>
							<div id="hk_text3">
								{{item.display_rate}}%
							</div>
							<div id="hk_text4">
								年利率
							</div>
							<div id="hk_text5">
								<div>投资期限</div>
								<div>借款总额</div>
							</div>
							<div id="hk_text6">
								<div>{{item.issue_count}}</div>
								<div>{{item.amount}}元</div>
							</div>
							<div id="hk_text7">
							<meter :value="item.progress"  min="0" max="100"></meter>
								<span>{{item.progress}}%</span>
							</div>
							<button class="btn"  id="hk_text8" @click="gobtnone(item)">{{item.status_display}}</button>

					</div>
				   </div>
				  </div>
				</div>
			</div>
		</div>
		
		
		
		<div class="homedivtwo">
			<div>
				<span>新标速递</span>
				<router-link tag="div" to="/investonehome" style="cursor: pointer;">
					<span>更多</span><img src="../../imgs/home/jiantouyi.png" alt="" />
				</router-link>
			</div>
			<div>
				<div id="imgidv">
					<img src="../../imgs/home/homeimgtwo.png"/>
				</div>
				
				<div id="hk_btextbox" class="swiper-containerd">
					<div class="swiper-wrapper">
						<div class="swiper-slide swiperwarp" v-for="(item,index) in newlist">
							<div class="swepersbox">
							<div class="biaoqianid" v-show="item.label_str!=''">
								<span>{{item.label_str}}</span>
							</div>
							<div id="hk_text1"> 
								<div>{{item.project_type_display}}</div>
								<div v-show="item.is_lock">锁</div>
							</div>
							<div id="hk_text2">
								{{item.name}}
							</div>
							<div id="hk_text3">
								{{item.display_rate}}%
							</div>
							<div id="hk_text4">
								年利率
							</div>
							<div id="hk_text5">
								<div>投资期限</div>
								<div>借款总额</div>
							</div>
							<div id="hk_text6">
								<div>{{item.issue_count}}</div>
								<div>{{item.amount}}元</div>
							</div>
							<div id="hk_text7">
							<meter :value="item.progress"  min="0" max="100"></meter>
								<span>{{item.progress}}%</span>
							</div>
							<button class="btn"  id="hk_text8" @click="gobtn(item)">{{item.status_display}}</button>
						
							</div>
						</div>
					</div>                                                       
				</div>
			</div>
		</div>
		<div id="homedivthree">
			<div id="homedivthreeleft">
				<div><span>行业资讯</span>
					<router-link tag="span" to="/messagetwo">
						<img src="../../imgs/home/jiantouyi.png"/>
					</router-link>
				</div>
				<div>
					<div class="bottomimgs">
						<!--<img v-for="item in hylist" :src="item.image" alt="" />-->
						<div v-for="item in hylist" class="bottomimgsbox">
							<a :href="item.url" v-if="item.url" target="_Blank">
								<img :src="item.image" alt="">
							</a>
							<img :src="item.image" alt="" @click="imgmessageitemtwo(item)">
						</div>
						
					
					</div>
					<div class="bottomdiv">
							<div v-for="item in hylist">{{item.title}}</div>
							<!-- <router-link tag="div" :to="'/messageitem/'+item.id" v-for="item in hylist">
							
							</router-link> -->

						
					</div>
					<div class="bottomdivtwo" >
						<div v-for="item in hylist">{{item.summary}}</div>
						<!-- <router-link tag="div" :to="'/messageitem/'+item.id" v-for="item in hylist">
						
						</router-link> -->
					</div>
				</div>
			</div>			
			<div id="homedivthreeright">
				<div> <span>站内公告</span>
					<router-link tag="span" to="/messageone">
						<img src="../../imgs/home/jiantouyi.png"/>
					</router-link>
					
				</div>
				<div>
					
					<ul id="homeulfrour">
						<li v-if="znlist==''"></li>
						<router-link v-else tag="li" :to="'/messageitem/'+item.id" v-for="item in znlist">
							<div></div>
							<div>{{item.title}}</div>
							<div>{{item.time.split("T")[0]}}</div>
						</router-link>
						
					</ul>
				</div>
			</div>
		</div>
		<!-- <div class="homedivfalst">
			<div>合作伙伴</div>
			<div>
				<a href="http://www.shihua365.cn/" target="_Blank">
					<img src="../../imgs/home/zu-16.png"/>
				</a>
				
				<a href="http://www.wdzj.com/" target="_Blank">
					<img src="../../imgs/home/zu-17.png"/>
				</a>
				<a href="http://www.gxgsl.com/" target="_Blank">
					<img src="../../imgs/home/zu-18.png"/>
				</a>
				<a href="http://baoxian.pingan.com/" target="_Blank">
					<img src="../../imgs/home/zu-19.png"/>
				</a>
				<a href="http://www.51zhengxin.com/front/" target="_Blank">
					<img src="../../imgs/home/zu-20.png"/>
				</a>
				<a href="https://www.95epay.com/" target="_Blank">
					<img src="../../imgs/home/zu-21.png"/>
				</a>
				
				
				
				
				
				
				<a href="http://www.cfca.com.cn/" target="_Blank">
					<img src="../../imgs/home/zu-22.png"/>
				</a>
			</div>
		</div> -->
	</div> 
	
	
	
	</div>
</template>

<script>
export default {
  data() {
    return {
      dataall: "", //全局数据
      data: "", //首页数据
      foreshowlist: "", //标预告
      newlist: "", //新标速递列表
      hylist: "", //行业咨询
      znlist: "", //站内公告
      showone: window.sessionStorage.token == undefined ? true : false, //banner的登陆的显示
      list: [
        "安全保障",
        "网贷工具",
        "帮助信息",
        "关于我们",
        "合作机构",
        "计算器工具",
        "帮助中心",
        "公司简介",
        "安全体系",
        "自动投标",
        "名词解释",
        "行业资讯",
        "网络协议",
        "资金明细",
        "网站公告",
        "政策法规",
        "计算器"
      ],
      imgurl: this.$url.ALIYUNCS,
      tybprojectlist: "" //体验标
    };
  },
  created() {
    window.sessionStorage.active = "0";
    window.sessionStorage.actives = "0";
    this.$http
      .post(this.$url.URL + this.$url.INDEX_DATA) //首页数据
      .then(response => {
        if (response.status == 200) {
          this.data = response.data;
          this.$nextTick(() => {
            var mySwipers = new Swiper(".swiper-container", {
              autoplay: 5000, //可选选项，自动滑动
              pagination: ".swiper-pagination", //分页器
              nextButton: ".swiper-button-next", //前后按钮
              prevButton: ".swiper-button-prev",
              loop: true,
              autoplayDisableOnInteraction: false
            });
          });
        } else {
          this.$notify({
            title: "警告",
            message: "请求数据出现错误",
            type: "warning"
          });
        }
      });
    if (window.sessionStorage.dataall == undefined) {
      this.$http
        .post(this.$url.URL + this.$url.AGLOBAL_DATA) //全局数据
        .then(response => {
          if (response.status == 200) {
            this.dataall = response.datadata;
            window.sessionStorage.dataall = JSON.stringify(response.data);
            window.sessionStorage.p = response.data.PLATFORM_MONEY_MORE_MORE;
          } else {
            this.$notify({
              title: "警告",
              message: "请求数据出现错误",
              type: "warning"
            });
          }
        });
    } else {
      this.dataall = JSON.parse(window.sessionStorage.dataall);
    }
    this.tybprojectlists();
    //标预告列表
    this.$http
      .get(this.$url.URL + this.$url.PREPROJECT) //标预告列表
      .then(res => {
        for (let i = 0; i < res.data.results.length; i++) {
          if (res.data.results[i].issue_type == "MONTH") {
            res.data.results[i].issue_count =
              res.data.results[i].issue_count + "个月";
          } else {
            res.data.results[i].issue_count =
              res.data.results[i].issue_count + "天";
          }
          if (res.data.results[i].progress < 100) {
            res.data.results[i].status_display = "立即投资";
          }
        }
        this.foreshowlist = res.data.results;
        this.$nextTick(() => {
          var mySwiper = new Swiper(".swiper-containers", {
            slidesPerView: 3,
            spaceBetween: 20,
            autoplay: 5000
          });
        });
      });
    //新标速递列表
    this.$http.get(this.$url.URL + this.$url.NEWPROJECT).then(res => {
      for (let i = 0; i < res.data.results.length; i++) {
        if (res.data.results[i].issue_type == "MONTH") {
          res.data.results[i].issue_count =
            res.data.results[i].issue_count + "个月";
        } else {
          res.data.results[i].issue_count =
            res.data.results[i].issue_count + "天";
        }
        if (res.data.results[i].progress < 100) {
          res.data.results[i].status_display = "立即投资";
        }
      }
      this.newlist = res.data.results;
      this.$nextTick(() => {
        var mySwiper = new Swiper(".swiper-containerd", {
          slidesPerView: 3,
          spaceBetween: 20,
          autoplay: 5000
        });
      });
    });
    //行业咨询
    this.$http.get(this.$url.URL + this.$url.ARTIVLELISTONE).then(response => {
      this.hylist = response.data.results;
      this.hylist.splice(3);
    });
    //站内公告
    this.$http.get(this.$url.URL + this.$url.ARTIVLELISTTWO).then(response => {
      this.znlist = response.data.results;
      this.znlist.splice(7);
    });
  },
  mounted(){
      $("html").height(1500);
      $("body").height(1500);
  },
  methods: {
    tybprojectlists() {
      this.$http.get(this.$url.URL + this.$url.TYBPROJECT).then(res => {
        for (let i = 0; i < res.data.results.length; i++) {
          if (res.data.results[i].issue_type == "MONTH") {
            res.data.results[i].issue_count =
              res.data.results[i].issue_count + "个月";
          } else {
            res.data.results[i].issue_count =
              res.data.results[i].issue_count + "天";
          }
          if (res.data.results[i].progress < 100) {
            res.data.results[i].status_display = "立即投资";
          }
        }
    this.tybprojectlist = res.data.results;
		this.$nextTick(() => {
			this.huoquhomeheight();
		})
		
      });
	},
	investonehomebtn(){
		this.$store.state.investonehomeindex="4"
		this.$router.push("/investonehome")
	},
    huoquhomeheight() {
	  var hdiv = $(".investonehome").height();
	  var hs = hdiv + 1230;
      $("html").height(hs);
      $("body").height(hs);
    },
    imgmessageitemtwo(item) {
      window.sessionStorage.actives = "1";
      this.$router.push({ path: "/messageitem/" + item.id });
    },
    gobtn(item) {
      this.$router.push({ path: "/invesdetails/" + item.id });
      sessionStorage.removeItem("particulars");
    },
    gobtnone(item) {
      this.$router.push({ path: "/invesdetails/" + item.id + "a" });
      sessionStorage.removeItem("particulars");
    }
  }
};
</script>

<style scoped="scoped" lang="less">
@import "../../../static/css/homecss/master.less";
.investonehomebox {
  width: 100%;
  overflow: hidden;
}
.investonehome {
  position: absolute;
  top: 660px;
  left: 50%;
  -webkit-transform: translateX(-50%);
  transform: translateX(-50%);
  width: 1200px;
  overflow: hidden;
  border-top: 1px solid #ffffff;
}
.homeulonebox {
  width: 100%;
  background-color: #ffffff;
}
.swipersdiv {
  width: 100%;
  height: 450px;
}
.swipersdiv > a {
  width: 100%;
  height: 100%;
}
.swipersdiv > a > img {
  width: 100%;
  height: 100%;
}
#homeulone {
  width: 1200px;
  height: 190px;
  background-color: #ffffff;

  margin: auto;
  overflow: hidden;
  & > li {
    width: 33.3333333%;
    height: 190px;
    float: left;
    text-align: center;
    background: url(../../imgs/home/leijidikuang.png) no-repeat 115px 48px;
    & > div:nth-of-type(1) {
      margin-top: 60px;
      font-size: 16px;
      color: #ffffff;
    }
    & > div:nth-of-type(2) {
      font-size: 26px;
      color: #d83515;
      margin-top: 30px;
      span {
        font-size: 16px;
        color: #666666;
      }
    }
  }
}
#homeultwo {
  width: 100%;
  background: #ffffff;
  overflow: hidden;
  margin: 0;
  padding: 50px 0;
  & > li {
    width: 33.3333333%;
    float: left;
    & > div {
      width: 90%;
      margin: auto;
      & > div {
        float: left;
      }
      & > div:nth-of-type(1) {
        width: 30%;
        img {
          vertical-align: middle;
        }
      }
      & > div:nth-of-type(2) {
        width: 65%;
        vertical-align: middle;
        margin-left: 5%;
        div {
          margin-left: 0;
        }
        & > div:nth-of-type(1) {
          font-size: 20px;
          width: 100%;
          margin-top: 15px;
          font-weight: bold;
        }
        & > div:nth-of-type(2) {
          font-size: 14px;
          width: 100%;
          margin-top: 10px;
        }
      }
    }
  }
}
#homedivone {
  width: 100%;
  background: #ffffff;
  margin-top: 20px;

  & > div:nth-of-type(1) {
    width: 100%;
    padding: 20px 0;
    span:nth-of-type(1) {
      font-size: 20px;
      color: #333333;
      vertical-align: middle;
      margin-left: 10px;
      margin-right: 30px;
      font-weight: bold;
    }
    & > span:nth-of-type(2) {
      cursor: pointer;
      font-size: 16px;
      color: #2f81fd;
      vertical-align: middle;
    }
    & > p {
      float: right;
      margin-right: 20px;
      cursor: pointer;
      & > span {
        font-size: 16px !important;
        color: #2f81fd !important;
        vertical-align: middle;
        margin-right: 10px !important;
        font-weight: normal !important;
      }
      & > img {
        vertical-align: middle;
      }
    }
  }
}
.texts {
  text-align: center !important;
  margin-left: 20px;
}
.texts > div:nth-of-type(1) {
  font-size: 16px;
  color: #333333;
}
.texts > div:nth-of-type(2) {
  font-size: 24px;
  color: #d83515;
  margin-top: 10px;
}
.texts > div:nth-of-type(2) > span {
  font-size: 16px;
  color: #666666;
}
.btntwo {
  width: 120px;
  height: 36px;
  color: #ffffff;
  position: absolute;
  bottom: 30px;
  right: 20px;
  font-size: 16px;
  background-color: @bkgrdtwo;
}
.homedivtwo {
  width: 100%;
  height: 430px;
  background-color: #ffffff;
  margin-top: 20px;
}
.homedivtwo > div:nth-of-type(1) {
  width: 100%;
  padding: 20px 0;
}
.homedivtwo > div:nth-of-type(1) > span {
  font-size: 20px !important;
  color: #333333;
  font-weight: bold;
  margin-left: 10px;
}
.homedivtwo > div:nth-of-type(1) > div {
  float: right;
  color: #2f81fd;
}
.homedivtwo > div:nth-of-type(1) > div > span {
  vertical-align: middle;
}
.homedivtwo > div:nth-of-type(1) > div > img {
  vertical-align: middle;
  margin-right: 20px;
  margin-left: 10px;
}
.homedivtwo > div:nth-of-type(2) {
  width: 100%;
}
#hk_btextbox {
  width: 850px;
  height: 360px;
  float: right;
  box-sizing: border-box;
  margin-top: -5px;
  overflow: hidden;
  margin-right: 10px;
}
.swepersbox {
  width: 94% !important;
  height: 350px;
  margin-left: 1%;
  float: left;
  box-shadow: 0px 0px 8px gainsboro;
  position: relative;
  border-bottom: 1px solid #ffffff;
  box-sizing: border-box;
  background-color: #ffffff;
  margin-top: 5px;
  margin-right: 0 !important;
  position: relative;
}
.biaoqianid {
  position: relative;
}
.ul_1 {
  width: 100%;
  > li:nth-last-of-type(1) > div {
    border: none;
  }
  > li {
    width: 100%;
    background: #ffffff;
    > div {
      margin: 0 30px;
      padding: 45px 0;
      border-bottom: 1px dotted #cacaca;
      overflow: hidden;
      > div:nth-last-of-type(1) {
        background-color: #ffffff;
        width: 138px;
        height: 42px;
        line-height: 42px;
        color: @bkgrdone;
        border: 1px solid @bkgrdone;
        text-align: center;
        border-radius: 10px;
        cursor: pointer;
      }
      > div:nth-of-type(1) {
        margin-right: 190px;
        color: #fd8f01;
      }
      > div:nth-of-type(2),
      div:nth-of-type(3),
      div:nth-of-type(4),
      div:nth-of-type(5) {
        margin-right: 60px;
        width: 100px;
        text-align: left;
      }

      > div {
        float: left;
        text-align: center;
        > p:nth-of-type(1) {
          font-size: 16px;
          margin-bottom: 8px;
        }
        > p:nth-of-type(2) {
          color: #999999;
        }
        > p {
          margin: 0;
          font-size: 12px;
        }
      }
    }
  }
}
.li_1:hover {
  transition: all 0.4s;
  width: 98%;
  // padding:-10px;
  margin: auto;
  margin-top: -2px;
  margin-bottom: 10px;
  box-shadow: 10px 10px 20px #e6e6e6;
  border-radius: 5px;
  > div {
    border: none;
    > div:nth-last-of-type(1) {
      background: @bkgrdone;
      color: #ffffff;
    }
  }
}
.biaoqianid span {
  position: absolute;
  right: 6px;
  top: 15px;
  display: inline-block;
  transform: rotate(45deg);
  color: #ffffff;
}
.biaoqianid::before {
  position: absolute;
  top: 0;
  right: 0;
  content: "";
  width: 0;
  height: 0;
  border-width: 40px;
  border-color: #ffc600 #ffc600 transparent transparent;
  border-style: solid;
}
.swipercontent {
  width: 100%;
  height: 450px;
}
#hk_text1 {
  width: 100%;
  margin-top: 8px;
}
#hk_text1 > div {
  float: left;
  font-size: 12px;
}
#hk_text1 > div:nth-of-type(1) {
  margin-left: 12px;
  padding:3px 10px;
  color: #ffffff;

  background-color: #14d1c1;
}
#hk_text1 > div:nth-of-type(2) {
  margin-left: 6px;
  width: 32px;
  height: 20px;
  line-height: 20px;
  text-align: center;
  color: #ffffff;
  background-color: #a1d513;
}
#hk_text2 {
  width: 100%;
  margin-top: 20px;
  text-align: center;
  font-size: 16px;
  color: #333333;
  font-weight: bold;
  float: left;
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
}
#hk_text3 {
  width: 100%;
  text-align: center;
  margin-top: 20px;
  font-size: 28px;
  color: #fd8f01;
  float: left;
}
#hk_text4 {
  width: 100%;
  float: left;
  color: #666666;
  font-size: 16px;
  margin-top: 5px;
  text-align: center;
}
#hk_text5 {
  width: 100%;
  margin-top: 20px;
  font-size: 14px;
  color: #333333;
  float: left;
}
#hk_text5 > div {
  float: left;
  width: 50%;
  text-align: center;
}
#hk_text6 {
  width: 100%;
  margin-top: 10px;
  font-size: 14px;
  color: #333333;
  float: left;
}
#hk_text6 > div {
  float: left;
  width: 50%;
  text-align: center;
}
#hk_text7 {
  margin-top: 20px;
  width: 100%;
  text-align: center;
  float: left;
  font-size: 14px;
}
meter {
  width: 160px;
  height: 12px;
  vertical-align: middle;
}
#hk_text7 > span {
  margin-left: 10px;
  vertical-align: middle;
}
#hk_text8 {
  width: 80%;
  height: 36px;
  line-height: 36px;
  text-align: center;
  margin-left: 10%;
  margin-top: 30px;
  float: left;
  background-color: @bkgrdone;
  color: #ffffff;
  font-size: 18px;
  border-radius: 6px;
  cursor: pointer;
}
.hk_bexttwo {
  background-color: #666666 !important;
}
.boxwiperwarp {
  width: 1200px;
  margin: auto;
  position: absolute;
  top: 0;
  left: 0;
  bottom: 0;
  right: 0;
  z-index: 0;
}
#imgidv {
  width: 310px;
  height: 350px;
  float: left;
}
#imgidv > img {
  width: 100%;
  height: 100%;
}
#homedivthree {
  width: 100%;
  height: 340px;
  margin-top: 20px;
}
.swiperwarp {
  width: 33.8%;
  text-align: center;
}
#homedivthreeleft {
  width: 720px;
  height: 340px;
  float: left;
  background-color: #ffffff;
}
#homedivthreeleft > div {
  width: 95%;
  margin: auto;
}
#homedivthreeleft > div:nth-of-type(1) {
  height: 60px;
  border-bottom: 1px solid #dcdcdc;
  box-sizing: border-box;
  line-height: 60px;
}
#homedivthreeright {
  width: 470px;
  height: 340px;
  float: left;
  margin-left: 10px;
  background-color: #ffffff;
}
#homedivthreeright > div {
  width: 95%;
  margin: auto;
}
#homedivthreeright > div:nth-of-type(1) {
  height: 60px;
  border-bottom: 1px solid #dcdcdc;
  box-sizing: border-box;
  line-height: 60px;
}
#homedivthreeleft > div:nth-of-type(2) {
  height: 280px;
}
#homedivthreeright > div:nth-of-type(2) {
  height: 280px;
}
#homedivthree > div > div:nth-of-type(1) > span {
  font-size: 20px;
  font-weight: bold;
}
#homedivthree > div > div:nth-of-type(1) > span > img {
  float: right;
  margin-top: 25px;
  margin-right: 10px;
  cursor: pointer;
}
.bottomimgs {
  margin-top: 20px;
  width: 100%;
  overflow: hidden;
  cursor: pointer;
}
.bottomimgs img {
  float: left;
  width: 31%;
  height: 150px;
  margin: 0 1%;
}

.bottomdiv {
  width: 100%;
  margin-top: 10px;
  overflow: hidden;
}
.bottomdiv > div {
  font-weight: bold;
  float: left;
  width: 32%;
  font-size: 14px;
  margin-top: 10px;
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
}
.bottomdiv > div:nth-of-type(2) {
  margin: 0 2%;
  margin-top: 10px;
}
bottomdiv > a {
  font-weight: bold;
  float: left;
  width: 32%;
  font-size: 14px;
  margin-top: 10px;
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
}
.bottomdiv > a:nth-of-type(2) {
  margin: 0 2%;
  margin-top: 10px;
}
.bottomdivtwo {
  margin-top: 6px;
  width: 100%;
  overflow: hidden;
  color: #999999;
}
.bottomdivtwo > div {
  float: left;
  width: 32%;
  font-size: 14px;
  height: 40px;
  overflow: hidden;
  text-overflow: ellipsis;
}
.bottomdivtwo > div:nth-of-type(2) {
  margin: 0 2%;
}
#homeulfrour {
  width: 100%;
}
#homeulfrour > li {
  width: 100%;
  height: 38px;
  cursor: pointer;
}
#homeulfrour > li:nth-of-type(1) {
  margin-top: 20px;
}
#homeulfrour > li > div {
  float: left;
}
#homeulfrour > li > div:nth-of-type(1) {
  width: 6px;
  height: 6px;
  border-radius: 50%;
  background-color: #2f81fd;
  margin-top: 8px;
  margin-left: 10px;
  margin-right: 10px;
}
#homeulfrour > li > div:nth-of-type(2) {
  width: 260px;
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
  font-size: 14px;
}
#homeulfrour > li > div:nth-of-type(3) {
  font-size: 12px;
  color: #999999;
  float: right;
  margin-right: 10px;
}
.homedivfalst {
  width: 100%;
  height: 145px;
  background-color: #ffffff;
  margin-top: 20px;
}
.homedivfalst > div:nth-of-type(1) {
  height: 60px;
  width: 100%;
  line-height: 60px;
  font-size: 20px;
  font-weight: bold;
  text-indent: 10px;
}
.homedivfalst > div:nth-of-type(2) {
  height: 85px;
  width: 100%;
}
.homedivfalst > div:nth-of-type(2) > a > img {
  float: left;
  margin-left: 10px;
}

.shade {
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.6);
  position: fixed;
  top: 0;
  left: 0;
}
.shadeboxs {
  width: 1060px;
  height: 580px;
  background: #ffffff;
  margin: 200px auto;
  position: relative;
  border-top: 1px solid #ffffff;
}
.shadeboxs > div {
  width: 1000px;
  height: 410px;
  margin: 100px auto;
  font-size: 16px;
}
.shadeboxs > img {
  position: absolute;
  right: 10px;
  top: 10px;
  cursor: pointer;
}
.boxswiperdiv {
  width: 300px;
  height: 370px;
  // float:right;
  // margin-top:40px;
  left: 50%;
  margin-left: 300px;
  top: 30px;
  background: rgba(0, 0, 0, 0.5);
  position: absolute;
  z-index: 999;
}
#boxswiperdivone {
  font-size: 14px;
  color: #fdfdfd;
  text-indent: 15px;
  padding-top: 20px;
}
#boxswiperdivtwo {
  font-size: 26px;
  color: #fd8f01;
  width: 100%;
  text-align: center;
  margin: 35px 0;
}
#boxswiperdivtwo > span {
  color: #ffffff;
}
#boxswiperdivthree {
  font-size: 20px;
  width: 100%;
  margin-bottom: 20px;
  text-align: center;
  color: #ffffff;
}
#boxswiperdivfour {
  font-size: 18px;
  width: 100%;
  margin-bottom: 30px;
  text-align: center;
  color: #ffffff;
}
.btnone {
  width: 250px;
  height: 40px;
  background-color: @bkgrdtwo;
  color: #ffffff;
  margin-left: 25px;
  font-size: 16px;
}
#boxswiperdivfive {
  width: 100%;
  text-align: center;
  margin-top: 30px;
  cursor: pointer;
}
#boxswiperdivfive > span {
  vertical-align: middle;
  color: #fdfdfd;
  font-size: 16px;
  margin-right: 14px;
}
#boxswiperdivfive > img {
  vertical-align: middle;
}
</style>