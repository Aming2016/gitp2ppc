<template>
  <div id="app">
  	<div class="tabtop">
  		<div class="tabtoptext">
  			<div>
  				<div id="tableft">
  					<div><img src="./imgs/mine/kufudianhua.jpg"/></div>
  					<div>客服热线 : </div>
  					<div> 0771-5771406</div>
  					<div class="weibo" @mouseenter="imgweixn=true" @mouseleave="imgweixn=false"><img src="./imgs/mine/weixin.jpg"/></div>
  					<!-- <div class="weibo" @mouseenter="imgweibo=true" @mouseleave="imgweibo=false"><img src="./imgs/mine/weibo.jpg"/></div> -->
  				</div>
  				
  				<div class="weixinewm" v-show="imgweixn">
		  			<img src="./imgs/home/bottotmApp.png"/>
		  			<div>扫描关注微信服务号</div>
		  		</div>
		  		
		  		<!-- <div class="weiboewm" v-show="imgweibo">
		  			<img src="./imgs/home/bottotmwebo.png"/>
		  			<div>扫描关注官方微博</div>
		  		</div> -->
		  		
		  		
		  	  				
  				
  				<div id="tabright" v-if="move">
  					<router-link tag="div" to="/register">立即登录</router-link>
  					<div>|</div>
  					<router-link tag="div" to="/logname">免费注册</router-link>
  					<div>|</div><router-link tag="div" to="/helpcentre">帮助中心</router-link>
  				</div>
  				
  				<div id="tabright" v-else="move">
  						
  						<router-link tag="div" to="/helpcentre">帮助中心</router-link>
  						<div ><!--<img src="./imgs/personal/xiaoxi.jpg"/>--><span><!--消息--></span><!--<div>2</div>--></div>
  						<router-link class="rabmovese" tag="div" to="/homeindex" >
  							<img src="./imgs/personal/zhanghuo1.jpg"/><span>欢迎{{name}}</span><img src="./imgs/personal/gengduosanjiaoxing.jpg"/>
  							<div class="dsj_move" v-show="movedsj"></div>
	  						<ul class="rabrightul">
	  							<li id="rebrightlione"></li>
	  							<router-link tag="li" to="/indexrecharge" class="movese1"><span>账户充值</span></router-link>
	  							<router-link tag="li" to="/indexstatistics" class="movese2"><span>我的投资</span></router-link>
	  							<router-link tag="li" to="/indexbill" class="movese3"><span>我的账单</span></router-link>
	  							<router-link tag="li" to="/indexaward" class="movese4"><span>邀请好友</span></router-link>
	  							<router-link tag="li" to="/" @click.native="dropout" class="movese5"><span>退出账户</span></router-link>
	  						</ul>
  						</router-link>
  						
  				</div>
  				<div id="photapp" @mouseover="imgapp=true" @mouseout="imgapp=false">
            <img src="./imgs/mine/shoujiapp.jpg"/>
  					<span>手机APP</span> 					
  						<div class="xiazaiapp" v-show="imgapp">			  			
                <img src="./imgs/home/bottomimgb.png"/>
				  			<div>扫描二维码下载APP</div>
				  		</div>

  				</div>
  			</div>
  		</div>
  		<div>  			
  		</div>
  		<div class="tablist">
  			<div> 
  				<ul id="tablistleft" @click="homebtnone">
  					<li></li>
  					<li>
  						<div>房产供应链金融领航者</div>
  						<div>轻松投资 | 乐享收益</div>
  					</li>
  				</ul>
  				<ul id="tablistright" >
  					<router-link tag="li" to="/" class="btnsli"  :class="{activeli:activeindex==1,tablistrightli:activeindex!==1}">首页</router-link>
  					<router-link tag="li" to="/investonehome" class="btnsli tablistrightli" :class="{activeli:activeindex==2}">投资中心</router-link>
  					<router-link tag="li" to="/borrowmoney" class="btnsli tablistrightli" :class="{activeli:activeindex==3}">借款通道</router-link>
  					<router-link tag="li" to="/newhand" class="btnsli tablistrightli" :class="{activeli:activeindex==4}">新手指引</router-link>
  					<router-link tag="li" to="/message" class="btnsli tablistrightli" :class="{activeli:activeindex==5}">信息资讯</router-link>
  					<router-link tag="li" to="/oneself" class="btnsli tablistrightli" :class="{activeli:activeindex==6}">关于我们</router-link>
  				</ul>
  			</div>
  		</div>
  		<ul class="appulindex">
  			<li v-if="moveone"><img src="./imgs/home/qiyelogo.png" style="zoom: 0.15;margin-top: 50px;"/></li>
  			<li v-else="moveone">
  				<div style="margin-top:25px;">温馨提示</div>
  			</li>
  			<li v-if="movetwo"><img src="./imgs/home/jisuanji.png"/></li>
  			<li v-else>
  				<div @click="btnjsq" style="margin-top:25px;">计算器</div>
  			</li>
  			<li v-if="movefive"><img  src="./imgs/home/erweima.png"/></li>
  			<li v-else="movefive">
  				<div style="margin-top:25px;">二维码</div>
  			</li>
  			<li v-if="movefour"><img src="./imgs/home/kefudianhua.png"/></li>
  			<li v-else="movefour">
  				<div style="margin-top:25px;">在线客服</div>
  			</li>
  			<li @click="btngo"><img src="./imgs/home/fanhuidingbuhei.png"/></li>
  		</ul>
  		<div class="diverweima" v-show="imgsewm" style="width: 260px;  height: 150px;bottom:112px;">
  			
  			<div style="float:right; margin-left: 10px;">
  				<img src="./imgs/home/bottomimgb.png" style="width:110px;height:110px;"/>
  				<div>二维码下载APP</div>
  			</div>
  			<div style="float:right;">
  				<img src="./imgs/home/yidianxianqian.jpg" style="width:110px;height:110px;"/>
  				<div>微信订阅号</div>
  			</div>
  			
  		</div>
  		<div class="diverweima" v-show="call" style="background-color: white;">
  				<ul>
  					<li style="margin-top:20px;">服务热线</li>
  					<li>0771-5771406</li>
  					<li>服务时间</li>
            <li>工作日</li>
  					<li>9:00-21:00</li>
  					<li style="color: red;margin-top: 5px;">联系我们</li>
  				</ul>
  		</div>
      <div class="diverweimad" v-show="callone">
        	<!-- <ul>
  					<li style="margin-top:20px;">服务热线</li>
  					<li>0771-5771406</li>
  					<li>服务时间</li>
            <li>工作日</li>
  					<li>9:00-21:00</li>
  					<li style="color: red;margin-top: 5px;">联系我们</li>
  				</ul> -->
          <br><br>
        投资有风险<br><br>
        理财需谨慎
  		</div>
  	</div>

  		
  		<div class="centers">
	  		<div>
	  			<router-view></router-view>
	  		</div>
  		</div>

  	
  	<div class="textbottom">
  		<div id="textbottomdiv">
  			<div>
  				<div>
  					<div class="divtop">
  						快速通道
  					</div>
  					<div class="divlistwarp">
  					
  						<!--<router-link tag="div" class="divleft_1" to="/">网贷工具</router-link>-->
  						<router-link tag="div" class="divleft_1" to="/oneself">关于我们</router-link>
  						<div class="divleft_1" @click="hezuobtn">合作机构</div>
  						<router-link tag="div" class="divleft_1" to="/helpcenone">帮助中心</router-link>
  						
  						<router-link tag="div" class="divleft_1" to="/oneself">公司简介</router-link>
  							<div class="divleft_1" @click="anquanbtn">安全保障</div>
  						<!--<router-link tag="div" class="divleft_1" to="/">安全体系</router-link>-->
  						<router-link tag="div" class="divleft_1" to="/helpcenthree">如何投资</router-link>
  							<router-link tag="div" class="divleft_1" to="/helpcefour">如何借款</router-link>
  							<router-link tag="div" class="divleft_1" to="/helpcenfive">如何充值</router-link>
  							<router-link tag="div" class="divleft_1" to="/helpcensix">如何提现</router-link>
  							<router-link tag="div" class="divleft_1" to="/helpcenseven">如何还款</router-link>
  							
  						<router-link tag="div" class="divleft_1" to="/messagetwo">行业资讯</router-link>
						  <div class="divleft_1" @click="wlxybtn">网络协议</div>
  						<router-link tag="div" class="divleft_1" to="/messageone">网站公告</router-link>
						  <div class="divleft_1" @click="wlxybtntwo">政策法规</div>
						<router-link tag="div" class="divleft_1" to="/calculator">计算器</router-link>
  					</div>				
  				</div>
	  			<div>
	  				<div class="divtop">
  						更多关注
  					</div>
  					<div class="divlistwarp2">
  							<div>
  								<div>
  									<img src="./imgs/home/bottomimgb.png"/>
  								</div>
  								<div>手机 APP</div>
  							</div>
  							<div>
  								<div>
  									<img src="./imgs/home/yidianxianqian.jpg"/>
  								</div>
  								<div>微信订阅号</div>
  							</div>
  					</div>
	  			</div>
	  			<div>
	  				<div class="divtop">
  						联系我们
  					</div>
            <div class="divtopleft">  
              <div>
                南宁总部
              </div>
              <div>
                总台客服：0771-5771406
              </div>
              <!-- <div>
                VIP专属客服A：17758670708
              </div>
              <div>
               VIP专属客服B：17758670722
              </div>
              <div>
                VIP专属客服C：17758670811
              </div>
              <div>
                VIP专属客服D：17758670755
              </div>
              <div>
                VIP专属客服E：17758670711
              </div> -->
              <div>
                客服管家：13977775731
              </div>
            </div>
            <div class="divtopright">
              <!-- <div>
                北海服务中心
              </div>
              <div>
                服务中心：0779-3838699
              </div>
              <div>
                贴心客服-小谭：15578797591
              </div>
              <div>
                贴心客服-小黎：13877984204
              </div>
              <div>
                贴心客服-小陆：18377959362
              </div> -->
            <div id="divright_4" @click="feedbacks">意见反馈</div>
            </div>
  					
	  			</div>
  			</div>
  			
  		</div>
  		<!-- <div id="textbottomdiv2">
  			
  			<a href="http://www.itrust.org.cn/" target="_Blank">
          <img src="../src/imgs/home/bottomfive.jpg"/>
        </a>
        <a href="https://www.pinpaibao.com.cn/" target="_Blank">
          <img src="../src/imgs/home/bottomimgfive.png"/>
        </a>
  			<a href="http://webscan.360.cn/" target="_Blank">
          <img src="../src/imgs/home/bottomone.png"/>
        </a>
        <a href="https://www.pinpaibao.com.cn/hyyz/?homenav" target="_Blank">
  			<img src="../src/imgs/home/bottomthree.png"/>
        </a>
        <a href="http://www.cecdc.com/" target="_Blank">
  			<img src="../src/imgs/home/bottomtwo.jpg"/>
        </a>
  		</div> -->
      <div class="textbottomdivfont">
        <div>
          <a target="view_window" href="http://si.trustutn.org/info?sn=737180625000651912086&certType=4">
          <img src="./imgs/home/bottomimgset.jpg" alt="">
          </a>
          <div>
            <div>总部地址：广西南宁市青秀区东葛路延长线118号青秀万达西1栋1406号</div>
            <div>北海服务中心：北海市海城区北海大道72号东旭华庭102号</div>
            <div>安全版本：V1.2.0</div>
          </div>
          
        </div>
  		</div>
  		<div id="textbottomdiv1">
  			<div>Copyright ©2016-2017 广西全民贷互联网金融信息咨询服务有限公司
  				<a href="http://www.miitbeian.gov.cn">桂ICP备18000542号-1</a>
  				 
  				 市场有风险 投资需谨慎</div>
  		</div>
  		
  	</div>
			<div class="feedbackwarp" v-show="feedback">
  			<div class="feedbackbox">
  				<div style="margin-left:2.5%;padding-top:30px;">请填写您的宝贵意见:</div>
  				<!--<div class="content" contenteditable="true" v-model="feedbackfont">
  					
  				</div>-->
  				<textarea name="" rows="" class="texttareabox" v-model="feedbackfont" cols=""></textarea>
  				<div class="submitbtnwarp">
  					<div @click="submitbtn" class="submitbtnclas">提交</div>
  				</div>
  				
  			</div>
  		</div>
  </div>
</template>

<script >
import router from "./router";

export default {
  name: "app",
  data() {
    return {
      activeindex: window.sessionStorage.activeindex,
      move: "",
      callone:false,
      imgweixn: false,
      imgweibo: false,
      imgapp: false,
      feedbackfont: "",
      movedsj: false,
      moveone: true,
      movetwo: true,
      movefour: true,
      movefive: true,
      imgsewm: false,
      name: null,
      call: false
    };
  },
  created() {
    window.sessionStorage.activelis = "0";
    var set = setInterval(() => {
      if (window.sessionStorage.token == undefined) {
        this.name = "";
        this.move = true;
      } else {
        this.name=JSON.parse(window.sessionStorage.getItem('myindexdata')).member_name;
        this.move = false;
      }
    }, 200);
  },
  computed: {
    //			shades(){
    //				return this.$store.state.shade
    //			},
    //			shadesone(){
    //				return this.$store.state.shadeone
    //			}
  },
  watch: {
    name() {
      this.name=JSON.parse(window.sessionStorage.getItem('myindexdata')).member_name;
    }
  },
  computed: {
    feedback() {
      return this.$store.state.opinion;
    }
  },
  methods: {
    dropout() {
      //退出账户
      window.location.reload();
      this.$router.push("/");
      sessionStorage.clear();
      localStorage.clear();
    },
    homebtnone(){
      this.$router.push("/")
    },
    btngo() {
      $(document).scrollTop(0);
    },
    wlxybtn() {
      window.sessionStorage.actives = "2";
      this.$router.push("/messagethree");
    },
    wlxybtntwo() {
      window.sessionStorage.actives = "3";
      this.$router.push("/messagefour");
    },
    feedbacks() {
      this.$store.dispatch("feedbacks");
    },
    btnjsq(){
    	this.$router.push("/calculator")
    },
    submitbtn() {
      if (this.feedbackfont !== "") {
        this.$http
          .post(this.$url.URL + this.$url.SUGGESTION, {
            content: this.feedbackfont
          })
          .then(res => {
            if (res.data.code == "0") {
              this.$alert("提交意见成功");
              this.feedbackfont = "";
            } else {
              this.$alert("提交意见失败");
            }
          })
          .catch(res => {
            this.$alert("提交意见失败");
          });
      }

      this.$store.dispatch("submitbtn");
    },

    //	  imgbtn(){
    //	  	this.$store.dispatch("imgbtn")
    //	  },
    //	  imgbtnone(){
    //	  	this.$store.dispatch("imgbtnone")
    //	  }
    anquanbtn() {
      this.$router.push("/oneself");
      setTimeout(() => {
        $(document).scrollTop(1530);
      }, 10);
    },
    hezuobtn() {
      this.$router.push("/");
      setTimeout(() => {
        $(document).scrollTop(2200);
      }, 10);
    }
  },
  mounted() {
    var that = this;
    var li = document.querySelectorAll(".appulindex>li");
    for (let i = 0; i < li.length; i++) {
      if (i == 0) {
        li[i].onmouseenter = function() {
          that.moveone = false;
          that.callone=true;
        };
        li[i].onmouseleave = function() {
          that.moveone = true;
          that.callone=false;
        };
      } else if (i ==1) {
        li[i].onmouseenter = function() {
          that.movetwo = false;
        };
        li[i].onmouseleave = function() {
          that.movetwo = true;
        };
      } else if (i == 2) {
        li[i].onmouseenter = function() {
          that.movefive = false;
          that.imgsewm = true;
        };
        li[i].onmouseleave = function() {
          that.movefive = true;
          that.imgsewm = false;
        };
      } else if (i == 3) {
        li[i].onmouseenter = function() {
          that.movefour = false;
           that.call = true;
        };
        li[i].onmouseleave = function(){
          that.movefour = true;
           that.call = false;
        };
      }
    }
    router.beforeEach((to, from, next) => {
      var path = to.path;
      var meta = document.querySelectorAll('meta');
      if (path == "/") {
        window.sessionStorage.activeindex = "1";
        that.activeindex = window.sessionStorage.activeindex;
        document.title = "全民金服-房产供应链金融服务平台";
        meta[1].content="投资理财, 全民金服, 网络投融资平台, 网络理财, 互联网理财, 个人理财, 房产贷,置业贷"
        meta[2].content="全民金服，房产供应链金融服务平台，提供安全、有保障的互联网投融资服务。为投资者提供房产贷、置业贷等优质理财产品，1000元起投,年化收益率高达14%。"
      } else if (path == "/investonehome") {
        window.sessionStorage.activeindex = "2";
        that.activeindex = window.sessionStorage.activeindex;
        document.title = "全民金服投资中心--房产供应链金融服务平台";
        meta[1].content="投资理财, 全民金服, 网络投融资平台, 网络理财, 互联网理财, 个人理财, 房产贷,置业贷"
        meta[2].content="全民金服投资中心频道为投资者提供房产贷、置业贷等优质理财产品，1000元起投,年化收益率高达14%，专业的在线投资理财团队，体验互联网金融魅力尽在全民金服。"
      } else if (path == "/borrowmoney") {
        window.sessionStorage.activeindex = "3";
        that.activeindex = window.sessionStorage.activeindex;
        document.title = "全民金服借款通道-房产供应链金融服务平台";
        meta[1].content="投资理财, 全民金服, 网络投融资平台, 网络理财, 互联网理财, 在线借款,个人理财, 房产贷,置业贷"
        meta[2].content="借款通道为用户提供快速融资贷款服务，用户通过在线申请，审核材料，实地考察，签署协议后，即可快速贷款。专业的融资服务团队，融资贷款首选全民金服，提供房产抵押贷款服务，10%-14%利率。"
        console.log(meta[1])
        console.log(meta[2])
      } else if (path == "/newhand") {
        window.sessionStorage.activeindex = "4";
        that.activeindex = window.sessionStorage.activeindex;
        document.title = "全民金服新手指引-房产供应链金融服务平台";
        meta[1].content="投资理财, 全民金服, 网络投融资平台, 网络理财, 互联网理财, 个人理财, 房产贷,置业贷"
        meta[2].content="全民金服通过新手指引为投资新手解答如何投资全民金服理财产品，投资本息、投资安全、担保、收益方式、周期、年化利率、充值等详细问题。"
      } else if (path == "/message") {
        window.sessionStorage.activeindex = "5";
        that.activeindex = window.sessionStorage.activeindex;
        document.title = "全民金服信息资讯-房产供应链金融服务平台";
        meta[1].content="投资理财, 全民金服, 网络投融资平台, 网络理财, 互联网理财, 个人理财, 房产贷,置业贷"
        meta[2].content="全民金服信息资讯频道涵盖P2P行业资讯、政策法规、网络协议以及官方公告和平台动态等内容，让你第一时间了解P2P行业最新最全的资讯新闻以及平台最新动态。"
      } else if (path == "/messageone") {
        window.sessionStorage.activeindex = "5";
        that.activeindex = window.sessionStorage.activeindex;
        document.title = "全民金服信息资讯-房产供应链金融服务平台";
        meta[1].content="投资理财, 全民金服, 网络投融资平台, 网络理财, 互联网理财, 个人理财, 房产贷,置业贷"
        meta[2].content="全民金服信息资讯频道涵盖P2P行业资讯、政策法规、网络协议以及官方公告和平台动态等内容，让你第一时间了解P2P行业最新最全的资讯新闻以及平台最新动态。"
      } else if (path == "/messagetwo") {
        window.sessionStorage.activeindex = "5";
        that.activeindex = window.sessionStorage.activeindex;
        document.title = "全民金服信息资讯-房产供应链金融服务平台";
        meta[1].content="投资理财, 全民金服, 网络投融资平台, 网络理财, 互联网理财, 个人理财, 房产贷,置业贷"
        meta[2].content="全民金服信息资讯频道涵盖P2P行业资讯、政策法规、网络协议以及官方公告和平台动态等内容，让你第一时间了解P2P行业最新最全的资讯新闻以及平台最新动态。"
      } else if (path == "/messagethree") {
        window.sessionStorage.activeindex = "5";
        that.activeindex = window.sessionStorage.activeindex;
        document.title = "全民金服信息资讯-房产供应链金融服务平台";
        meta[1].content="投资理财, 全民金服, 网络投融资平台, 网络理财, 互联网理财, 个人理财, 房产贷,置业贷"
        meta[2].content="全民金服信息资讯频道涵盖P2P行业资讯、政策法规、网络协议以及官方公告和平台动态等内容，让你第一时间了解P2P行业最新最全的资讯新闻以及平台最新动态。"
      } else if (path == "/messagefour") {
        window.sessionStorage.activeindex = "5";
        that.activeindex = window.sessionStorage.activeindex;
        document.title = "全民金服信息资讯-房产供应链金融服务平台";
        meta[1].content="投资理财, 全民金服, 网络投融资平台, 网络理财, 互联网理财, 个人理财, 房产贷,置业贷"
        meta[2].content="全民金服信息资讯频道涵盖P2P行业资讯、政策法规、网络协议以及官方公告和平台动态等内容，让你第一时间了解P2P行业最新最全的资讯新闻以及平台最新动态。"
      } else if (path == "/messageitem") {
        window.sessionStorage.activeindex = "5";
        that.activeindex = window.sessionStorage.activeindex;
        document.title = "全民金服信息资讯-房产供应链金融服务平台";
        meta[1].content="投资理财, 全民金服, 网络投融资平台, 网络理财, 互联网理财, 个人理财, 房产贷,置业贷"
        meta[2].content="全民金服信息资讯频道涵盖P2P行业资讯、政策法规、网络协议以及官方公告和平台动态等内容，让你第一时间了解P2P行业最新最全的资讯新闻以及平台最新动态。"
      } else if (path == "/messagefive") {
        window.sessionStorage.activeindex = "5";
        that.activeindex = window.sessionStorage.activeindex;
        document.title = "全民金服信息资讯-房产供应链金融服务平台";
        meta[1].content="投资理财, 全民金服, 网络投融资平台, 网络理财, 互联网理财, 个人理财, 房产贷,置业贷"
        meta[2].content="全民金服信息资讯频道涵盖P2P行业资讯、政策法规、网络协议以及官方公告和平台动态等内容，让你第一时间了解P2P行业最新最全的资讯新闻以及平台最新动态。"
      } else if (path == "/oneself") {
        window.sessionStorage.activeindex = "6";
        that.activeindex = window.sessionStorage.activeindex;
        document.title = "全民金服关于我们-房产供应链金融服务平台";
        meta[1].content="投资理财, 全民金服, 网络投融资平台, 网络理财, 互联网理财, 个人理财, 房产贷,置业贷"
        meta[2].content="全民金服，房产供应链金融服务平台，提供安全、有保障的互联网投融资服务。为投资者提供房产贷、置业贷等优质理财产品，1000元起投,年化收益率高达14%。"
      } else if (path == "/helpcenone") {
        document.title = "全民金服帮助中心-房产供应链金融服务平台";
        meta[1].content="投资理财, 全民金服, 网络投融资平台, 网络理财, 互联网理财, 个人理财, 房产贷,置业贷"
        meta[2].content="全民金服，房产供应链金融服务平台，提供安全、有保障的互联网投融资服务。为投资者提供房产贷、置业贷等优质理财产品，1000元起投,年化收益率高达14%。"
      } else if (path == "/helpcentwo") {
        document.title = "为什么选择我们-房产供应链金融服务平台";
        meta[1].content="投资理财, 全民金服, 网络投融资平台, 网络理财, 互联网理财, 个人理财, 房产贷,置业贷"
        meta[2].content="全民金服，房产供应链金融服务平台，提供安全、有保障的互联网投融资服务。为投资者提供房产贷、置业贷等优质理财产品，1000元起投,年化收益率高达14%。"
      }else if (path == "/helpcenthree") {
        document.title = "如何投资-房产供应链金融服务平台";
        meta[1].content="投资理财, 全民金服, 网络投融资平台, 网络理财, 互联网理财, 个人理财, 房产贷,置业贷"
        meta[2].content="全民金服，房产供应链金融服务平台，提供安全、有保障的互联网投融资服务。为投资者提供房产贷、置业贷等优质理财产品，1000元起投,年化收益率高达14%。"
      }else if (path == "/helpcefour") {
        document.title = "如何借款-房产供应链金融服务平台";
        meta[1].content="投资理财, 全民金服, 网络投融资平台, 网络理财, 互联网理财, 个人理财, 房产贷,置业贷"
        meta[2].content="全民金服，房产供应链金融服务平台，提供安全、有保障的互联网投融资服务。为投资者提供房产贷、置业贷等优质理财产品，1000元起投,年化收益率高达14%。"
      }else if (path == "/helpcenfive") {
        document.title = "如何充值-房产供应链金融服务平台";
        meta[1].content="投资理财, 全民金服, 网络投融资平台, 网络理财, 互联网理财, 个人理财, 房产贷,置业贷"
        meta[2].content="全民金服，房产供应链金融服务平台，提供安全、有保障的互联网投融资服务。为投资者提供房产贷、置业贷等优质理财产品，1000元起投,年化收益率高达14%。"
      }else if (path == "/helpcensix") {
        document.title = "如何提现-房产供应链金融服务平台";
        meta[1].content="投资理财, 全民金服, 网络投融资平台, 网络理财, 互联网理财, 个人理财, 房产贷,置业贷"
        meta[2].content="全民金服，房产供应链金融服务平台，提供安全、有保障的互联网投融资服务。为投资者提供房产贷、置业贷等优质理财产品，1000元起投,年化收益率高达14%。"
      }else if (path == "/helpcenseven") {
        document.title = "如何还款-房产供应链金融服务平台";
        meta[1].content="投资理财, 全民金服, 网络投融资平台, 网络理财, 互联网理财, 个人理财, 房产贷,置业贷"
        meta[2].content="全民金服，房产供应链金融服务平台，提供安全、有保障的互联网投融资服务。为投资者提供房产贷、置业贷等优质理财产品，1000元起投,年化收益率高达14%。"
      }else if (path == "/helpcennine") {
        document.title = "常见问题-房产供应链金融服务平台";
        meta[1].content="投资理财, 全民金服, 网络投融资平台, 网络理财, 互联网理财, 个人理财, 房产贷,置业贷"
        meta[2].content="全民金服，房产供应链金融服务平台，提供安全、有保障的互联网投融资服务。为投资者提供房产贷、置业贷等优质理财产品，1000元起投,年化收益率高达14%。"
      }else {
        sessionStorage.removeItem("activeindex");
        that.activeindex = null;
        document.title = "全民金服";
      }
      next();
    });

    //			for(let i=0;i<$(".tablistrightli").length;i++){
    //				console.log($(".tablistrightli").eq(i).css("color"))
    //				if($(".tablistrightli").eq(i).css("color")=="rgb(51, 51, 51)"){
    //
    //				$(".tablistrightli").eq(i).mouseenter(function(){
    //					console.log($(".tablistrightli").eq(i).css("color"))
    //					$(this).css({
    //						color:"#FD8F01"
    //					})
    //					$(".tablistrightli").eq(i).mouseleave(function(){
    //						$(this).css({
    //							color:"#333333"
    //						})
    //					})
    //				})
    //
    //				}
    //			}

    $(".rabrightul").mouseenter(function() {
      that.movedsj = true;
      $(".rabrightul").animate({
        height: "190px"
      });
    });
    $(".rabrightul").mouseleave(function() {
      $(".rabrightul").animate({
        height: "38px"
      });
      setTimeout(function() {
        that.movedsj = false;
      }, 300);
    });

    var lastTime = new Date().getTime(); //自动推出登录
    var currentTime = new Date().getTime();
    var timeOut =30*60*1000; //设置超时时间： 30分

    $(function() {
      /* 鼠标移动事件 */
      $(document).mouseover(function(){
        lastTime = new Date().getTime(); //更新操作时间
      });
    });
    var setidong= setInterval(() => {
      currentTime = new Date().getTime(); //更新当前时间
      if (currentTime - lastTime > timeOut) {
        //判断是否超时
        if(window.sessionStorage.token){
          clearInterval(setidong)
          sessionStorage.clear();
          this.$router.push("/register");
          window.location.reload();
        }
        
      }
    }, 1000);  


    //百度统计
    var _hmt = _hmt || [];
    (function() {
      var hm = document.createElement("script");
      hm.src = "https://hm.baidu.com/hm.js?bcf1f6fd514f9e26a329d8b3d521b8a2";
      var s = document.getElementsByTagName("script")[0]; 
      s.parentNode.insertBefore(hm, s);
    })();
    // function testTime(){
    // 	currentTime = new Date().getTime(); //更新当前时间
    // 	if(currentTime - lastTime > timeOut){ //判断是否超时
    // 	sessionStorage.clear();
    // 	this.$router.push('/register')
    // 	window.location.reload();

    // 	}
    // }
    // /* 定时器  间隔1秒检测是否长时间未操作页面  */
    // window.setInterval(testTime, 1000);
  }
};
</script>

<style lang="less">
@import "../static/css/homecss/master.less";
.el-carousel__item h3 {
  color: #475669;
  font-size: 14px;
  opacity: 0.75;
  margin: 0;
}

.el-carousel__item:nth-child(2n) {
  background-color: #99a9bf;
}

.el-carousel__item:nth-child(2n + 1) {
  background-color: #d3dce6;
}

#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  width: 100%;
}

* {
  margin-top: 0;
  padding: 0;
  font-family: "Microsoft YaHei" !important;
}
ul {
  list-style: none;
}

#indextext {
  color: #333333;
  font-size: 18px;
  font-weight: bold;
  height: 30px;
  border-bottom: 2px solid #333333;
  width: 75px;
  box-sizing: border-box;
}
.indexmessage {
  width: 100%;
  position: absolute;
  top: 0;
  left: 0;
  background-color: #ffffff;
  overflow: hidden;
}
input {
  border: 1px solid #cacaca;
  border-radius: 6px;
  outline: none;
}

#indexdataright {
  width: 970px;
  margin: auto;
}
#indexdatatop {
  width: 100%;
  height: 30px;
  border-bottom: 2px solid #cacaca;
  box-sizing: border-box;
  margin-top: 20px;
}
#indexdatatop > div:nth-of-type(1) {
  float: left;
}
#indexdatatop > div:nth-of-type(2) {
  float: right;
  color: #ffc600;
  font-size: 14px;
  cursor: pointer;
}
.btn {
  background-color: #ffc600;
  border: none;
  border-radius: 6px;
  outline: none;
  cursor: pointer;
}

.tabtop {
  width: 100%;
  position: absolute;
  top: 0;
  left: 0;
  height: 140px;
}

.tabtoptext {
  width: 100%;
  height: 40px;
  background-color: #3e3e3e;
  border-top: 1px solid #3e3e3e;
  box-sizing: border-box;
  z-index: 999;
  clear: both;
}
.tablist {
  width: 100%;
  height: 100px;
  border-top: 1px solid #ffffff;
  box-sizing: border-box;
  box-shadow: 0px 4px 6px gainsboro;
  background-color: #ffffff;
}
.centers {
  width: 100%;
  position: absolute;
  top: 140px;
  background-color: #f5f5f5;
}
.centers > div {
  width: 100%;
  position: relative;
}
.tabtoptext > div {
  width: 1200px;
  height: 100%;
  margin: auto;
  z-index: 999;
  position: relative;
}
.tablist > div {
  width: 1200px;
  height: 100%;
  margin: auto;
}
#tablistleft {
  float: left;
  list-style: none;
}
#tablistleft > li {
  display: inline-block;
}
#tablistleft > li:nth-of-type(1) {
  width: 190px;
  height: 82px;
  margin-top:-5px;
  float: left;
  background: url(imgs/mine/logotwo.png) no-repeat 100% 100%;
}
#tablistleft > li:nth-of-type(2) {
  margin-left: 20px;
  float: left;
  margin-top: 30px;
  text-align: center;
}
#tablistleft > li:nth-of-type(2) > div:nth-of-type(1) {
  font-size: 14px;
  color: #3e3e3e;
}
#tablistleft > li:nth-of-type(2) > div:nth-of-type(2) {
  font-size: 16px;
  color: #3e3e3e;
}
#tableft {
  height: 100%;
  float: left;
}
#tableft > div {
  height: 100%;
  float: left;
  line-height: 40px;
}
#tableft > div > img {
  padding-top: 9px;
}
#tableft > div:nth-of-type(2) {
  color: #ffffff;
  margin-left: 10px;
  font-size: 14px;
  text-align: center;
}
#tableft > div:nth-of-type(3) {
  color: white;
  font-size: 20px;
  margin-left: 5px;
  text-align: center;
}
#tableft > div:nth-of-type(4),
#tableft > div:nth-of-type(5) {
  margin-left: 20px;
}
#tabright {
  float: right;
  height: 40px;
  line-height: 40px;
  position: relative;
}
#tabright > div {
  display: inline-block;
  color: #ffffff;
  font-size: 14px;
  margin-left: 10px;
  cursor: pointer;
}
#tabright > div > img {
  vertical-align: middle;
}
#tabright > div > span {
  vertical-align: middle;
}
#tabright > div:nth-of-type(2) {
  border: 1px solid #3e3e3e;
  box-sizing: border-box;
  margin: 0 5px;
  border: none;
}
#tabright > div:nth-of-type(2) > span {
  margin: 0 5px;
  color: #ffc600;
}
#tabright > div:nth-of-type(2) > div {
  width: 25px;
  height: 25px;
  border-radius: 50%;
  text-align: center;
  line-height: 26px;
  background-color: #ffc600;
  display: inline-block;
  float: right;
  margin-top: 8px;
}
.rabmovese > span {
  color: #ffc600;
  margin: 0 5px;
}
#photapp {
  width: 90px;
  height: 28px;
  line-height: 22px;
  font-size: 12px;
  color: #ffc600;
  float: right;
  border: 1px solid #ffc600;
  border-radius: 6px;
  margin-top: 5px;
  margin-right: 15px;
  text-align: center;
  box-sizing: border-box;
  cursor: pointer;
  position: relative;
}
#photapp > img {
  vertical-align: middle;
}
#photapp > span {
  vertical-align: middle;
  margin-left: 5px;
}
#tablistright {
  float: right;
  height: 40px;
  margin-top: 30px;
}
.tablistrightli:hover {
  /*font-size:22px;*/
  margin-top: -3px;
}
.tablistrightli {
  display: inline-block;
  height: 100%;
  line-height: 40px;
  padding: 0 20px;
  float: left;
  border-radius: 8px;
  color: #333333;
  font-size: 20px;
  cursor: pointer;
}

.activeli {
  color: #ffffff;
  background-color: @bkgrdone;
}
.textbottom {
  position: absolute;
  bottom: 0;
  left: 0;
  width: 100%;
  height: 400px;
  margin-top: 20px;
  border-top: 1px solid #3e3e3e;
  box-sizing: border-box;
  z-index: 444;
}
.textbottom > div {
  width: 1200px;
  height: 350px;
  margin: auto;
  position: relative;
}
#textbottomdiv > div > div {
  float: left;
}
#textbottomdiv {
  background-color: #3e3e3e;
  width: 100%;
  /*height:320px;*/
}
#textbottomdiv > div {
  width: 1200px;
  height: 320px;
  margin: auto;
  border-top: 1px solid #3e3e3e;
  box-sizing: border-box;
  position: relative;
}
#textbottomdiv > div > div:nth-of-type(1) {
  width: 35%;
  height: 100%;
}
#textbottomdiv > div > div:nth-of-type(2) {
  width:19%;
  height: 100%;
  margin-left:5%;
}
#textbottomdiv > div > div:nth-of-type(3) {
  width: 38%;
  height: 100%;
  margin-left:3%;
}
#textbottomdiv1 {
  width: 100%;
  height: 50px;
  background-color: #000000;
  text-align: center;
  line-height: 50px;
  color: #ffffff;
  font-size: 14px;
}
#textbottomdiv1 > div {
  width: 1200px;
  margin: auto;
  height: 100%;
}
.divtop {
  height: 35px;
  width: 84px;
  border-bottom: 1px solid #ffffff;
  margin-top: 60px;
  font-size: 20px;
  color: #FFFFFF;
}
.divtopleft{
  width:50%;
  // height:100px;
  float:left;
  margin-top:25px;
  font-size:14px;
  color:#D1D1D1;
}
.divtopleft>div:nth-of-type(1){
  color:#ffffff;
  font-size:16px;
  margin-bottom:5px;
}
.divtopright{
  width:50%;
  float:right;
  margin-top:25px;
  font-size:14px;
  color:#D1D1D1;
}
.divtopright>div{
  margin-bottom:3px;
}
.divtopleft>div{
  margin-bottom:3px;
}
.divtopright>div:nth-of-type(1){
  margin-bottom:5px;
  color:#ffffff;
  font-size:16px;
}
.divleft_1 {
  width: 25%;
  float: left;
  text-align: center;
}
.divlistwarp > div:nth-of-type(4n + 1) {
  text-align: left;
}
.divlistwarp > div:nth-of-type(4n) {
  text-align: right;
}
.divlistwarp {
  margin-top: 25px;
  font-size: 14px;
  color: #ffffff;
  cursor: pointer;
}
.divlistwarp > div:nth-of-type(n + 5) {
  margin-top: 20px;
}
.divlistwarp2 {
  margin-top: 25px;
  font-size: 16px;
  color: #ffffff;
}
.divlistwarp2 > div {
  width: 100px;
  float: left;
}
.divlistwarp2 > div:nth-of-type(2) {
  width: 100px;
  // margin-left:10%;
  float:right;
}
.divlistwarp2 > div > div:nth-of-type(1) {
  width: 100px;
  height: 100px;
  margin: auto;
}
.divlistwarp2 > div > div:nth-of-type(1) > img {
  width: 100%;
  height: 100%;
}
.divlistwarp2 > div > div:nth-of-type(2) {
  width: 100%;
  text-align: center;
  margin-top: 15px;
}
#divright_4 {
  width: 167px;
  height: 40px;
  background-color: #2f81fd;
  text-align: center;
  line-height: 40px;
  color: #ffffff;
  float: right;
  margin-top: 20px;
  margin-right:40px;
  border-radius: 6px;
  cursor: pointer;
}
.weibo {
  cursor: pointer;
}
.dsj_move {
  width: 10px;
  height: 10px;
  background-color: #f5f5f5;
  position: absolute;
  bottom: -5px;
  right: 60px;
  -webkit-transform: rotate(45deg);
  -moz-transform: rotate(45deg);
  -ms-transform: rotate(45deg);
  -o-transform: rotate(45deg);
  transform: rotate(45deg);
}
.rabrightul {
  list-style: none;
  width: 104px;
  position: absolute;
  height: 38px;
  top: 0px;
  right: 15px;
  color: #ffffff;
  font-size: 14px;

  z-index: 11111;
  overflow: hidden;
}
#rebrightlione {
  width: 100%;
  height: 40px;
  opacity: 0;
  z-index: 999;
}
.rabrightul > li > span {
  vertical-align: middle;
  margin-left: 25px;
}

.rabrightul > li {
  width: 100%;
  height: 30px;
  line-height: 30px;
  z-index: 888;
  text-align: center;
  color: #333333;
  cursor: pointer;
  background-color: #f5f5f5;
}
.movese1 {
  background: url(./imgs/personal/zhanghuchongzhi.jpg) no-repeat 12px 8px;
}
.movese2 {
  background: url(./imgs/personal/wodetouzi.jpg) no-repeat 12px 8px;
}
.movese3 {
  background: url(./imgs/personal/wodejiekuan.jpg) no-repeat 12px 8px;
}
.movese4 {
  background: url(./imgs/personal/haoyouyaoqing.jpg) no-repeat 12px 8px;
}
.movese5 {
  background: url(./imgs/personal/tuichuzhanghu.jpg) no-repeat 12px 8px;
}
.movese1:hover {
  background: url(./imgs/personal/zhanghuchongzhi1.jpg) no-repeat 12px 8px;
  color: #ffc600;
  background-color: #f5f5f5;
}
.movese2:hover {
  background: url(./imgs/personal/wodetouzi1.jpg) no-repeat 12px 8px;
  color: #ffc600;
  background-color: #f5f5f5;
}
.movese3:hover {
  background: url(./imgs/personal/wodejiekuan1.jpg) no-repeat 12px 8px;
  color: #ffc600;
  background-color: #f5f5f5;
}
.movese4:hover {
  background: url(./imgs/personal/haoyouyaoqing1.jpg) no-repeat 12px 8px;
  color: #ffc600;
  background-color: #f5f5f5;
}
.movese5:hover {
  background: url(./imgs/personal/tuichuzhanghu1.jpg) no-repeat 12px 8px;
  color: #ffc600;
  background-color: #f5f5f5;
}
.boxswiper {
  width: 100%;
  height: 500px;
  overflow: hidden;
  position: absolute;
  top: 140px;
}
.swiper-container {
  width: 100%;
  height: 100%;
  z-index: 888;
}

.appulindex {
  width: 80px;
  height:360px;
  position: fixed;
  bottom:29px;
  right: 10px;
  z-index: 9999;
  cursor: pointer;
  border: 1px solid #dcdcdc;
  box-shadow: 0 0 6px gainsboro;
}
.appulindex > li {
  width: 100%;
  height: 20%;
  float: left;
  background-color: #ffffff;
  border-bottom: 1px solid #dcdcdc;
  box-sizing: border-box;
  text-align: center;
  color: #ffffff;
  font-size: 14px;
}
.appulindex > li:nth-last-of-type(1) {
  border: none;
}
.appulindex > li > img {
  margin-top: 15px;
}
.appulindex > li:nth-last-of-type(1) > img {
  margin-top: 25px;
}
.appulindex > li:hover {
  background-color: #ffc600;
}
.diverweima {
  min-width: 150px;
  height: 190px;
  background-color: #ffc600;
  position: fixed;
  bottom:0px;
  right: 92px;
  text-align: center;
  z-index: 999;
}
.diverweimad{
  min-width: 150px;
  height: 160px;
  background-color: #ffc600;
  position: fixed;
  bottom:246px;
  right: 92px;
  color:#ffffff;
  text-align: center;
  z-index: 999;
}
.diverweima > img {
  padding-top:20px;
  display: inline-block;
}
.diverweima > div {
  margin-right:10px;
  font-size: 14px;
  color: #ffffff;
  margin-top: 10px;
  float:left;
  margin-left:0;
}
.diverweima > div :nth-of-type(1){
  margin-right:0;
  // margin-left:10px;
}
.diverweima > div :nth-of-type(2){
  // margin-right:0;
  margin-left:0;
}
.xiazaiapp {
  width: 150px;
  height: 190px;
  background-color: #ffc600;
  position: absolute;
  top: 33px;
  left: -30px;
  text-align: center;
  z-index: 100000;
}
.xiazaiapp > img {
  padding-top: 20px;
  width: 80%;
}
.xiazaiapp > div {
  font-size: 14px;
  color: #ffffff;
  margin-top: 10px;
}

.weiboewm {
  width: 150px;
  height: 190px;
  background-color: #ffc600;
  position: absolute;
  top: 39px;
  left: 232px;
  text-align: center;
  z-index: 999;
  /*display: block !important;*/
}
.weiboewm > img {
  padding-top: 20px;
  width: 80%;
}
.weiboewm > div {
  font-size: 14px;
  color: #ffffff;
  margin-top: 10px;
}
.weixinewm {
  width: 150px;
  height: 190px;
  background-color: #ffc600;
  position: absolute;
  top: 39px;
  left: 190px;
  text-align: center;
  z-index: 999;
}
.weixinewm > img {
  padding-top: 20px;
  width: 80%;
}
.weixinewm > div {
  font-size: 14px;
  color: #ffffff;
  margin-top: 10px;
}

.shade {
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.6);
  position: fixed;
  top: 0;
  left: 0;
}
.shadebox {
  width: 900px;
  height: 230px;
  background: #ffffff;
  margin: 300px auto;
  position: relative;
  border-top: 1px solid #ffffff;
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
.shadebox > img {
  position: absolute;
  right: 10px;
  top: 10px;
  cursor: pointer;
}
.shadecenter {
  width: 700px;
  height: 150px;
  margin: 30px auto;
  font-size: 16px;
}
.shadecenter > div {
  width: 50%;
  float: left;
  margin-top: 30px;
}
a {
  color: #ffffff;
  text-decoration: none;
}
#textbottomdiv2 {
  width: 100%;
  height: 60px;
  background-color: #3e3e3e;
  text-align: center;
  position: relative;
}
#textbottomdiv2 > a > img {
  width: 100px;
  height:40px;
  margin-left: 30px;
}
#textbottomdiv2 > a > img:nth-of-type(1) {
  margin: 0;
}
.textbottomdivfont {
  width: 100% !important;
  text-align: center;
  height:80px !important;
  background:#3E3E3E;
  color:#ffffff;
  font-size:14px !important;  
  padding-bottom:10px;
  position: relative !important;
}
.textbottomdivfont>div{
  width:1200px;
  margin:auto;
  // text-align: center; 
  overflow: hidden;
}
.textbottomdivfont>div>div{
  margin-bottom:5px;
  display: inline-block;
  vertical-align: middle;
  margin-left:50px;
  text-align: left;
}
.textbottomdivfont>div>div>div{
  line-height:1.5;
}
.textbottomdivfont>div>a>img{
  vertical-align: middle;
  width:150px;
  // margin-left:50px;
}
.textbottomdivfonts {
  position: absolute;
  bottom: -20px;
  right: 110px;
  color: #ffffff;
}
.feedbackwarp {
  width: 100%;
  height: 100%;
  position: fixed;
  top: 0;
  left: 0;
  background: rgba(0, 0, 0, 0.6);
  z-index: 999999;
}
.feedbackbox {
  width: 50%;
  height: 420px;
  min-width: 900px;
  background-color: #ffffff;
  margin: auto;
  position: absolute;
  top: 0;
  left: 0;
  bottom: 0;
  right: 0;
}
.texttareabox {
  width: 90%;
  height: 260px;
  margin-left: 4%;
  margin-top: 10px;
  border: 1px solid #333333;
  border-radius: 6px;
  text-indent: 20px;
  padding: 10px;
  word-break: keep-all;
  resize: none;
}
.submitbtnwarp {
  width: 100%;
}
.submitbtnclas {
  width: 100px;
  height: 40px;
  text-align: center;
  line-height: 40px;
  background-color: #007aff;
  color: #ffffff;
  border-radius: 6px;
  float: right;
  cursor: pointer;
  margin-right: 4%;
}
</style>
