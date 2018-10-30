<template>
	<div class="indexmoney">
		<!-- <ul class="indexmoneyul">
			<li id="indexoneli">投资统计</li>
			<li>
				<div>预投金额</div>
				<div>在投金额</div>
				<div>投资收益</div>
				<div>邀请奖励</div>
				<div>其他收益</div>
			</li>
			<li>
				<div>{{this.investment_statistics.pre_invest_amount}}</div>
				<div>￥{{this.investment_statistics.investing_amount}}</div>
				<div>￥{{this.investment_statistics.invest_income_amount}}</div>
				<div>￥{{this.investment_statistics.invite_award}}</div>
				<div>￥{{this.investment_statistics.other_amount}}</div>
			</li>
		</ul> -->
		<div id="indexmoneydiv_1">
			我的预投
		</div>
		<div id="indexmoneydiv">
			<div v-for="(item,index) in list" @click="indexidbtn(index)" :class="{moveclass:indexid==index}">{{item}}</div>			
		</div>
		<div id="indexmoneybox">

			<!--待支付-->
			<div v-if="indexid==0">
				<div class="indexboxbaber">
					<div>项目名称</div>
					<div>预投金额</div>
					<div>投资期限</div>
					<div>回款方式</div>
					<div>投资日期</div>
					<div>年利率</div>
					<div>预计发标时间</div>
					<div>操作</div>
				</div>
				<ul class="indexboxul">
          <li class="indexboxli" v-for="(item,index) in dataone" @click="dataonebtntwo(item)">
						<div class="itemdiv">{{item.name}}</div>
						<div>{{item.amount}}元</div>
						<div>{{item.issue_count}}</div>
						<div>{{item.repay_type_display}}</div>
						<div>{{item.time.split(' ')[0]}}</div>
						<div>{{item.rate}}%</div>
						<div>{{item.kaibiao_date.split(" ")[0]}}</div>
						<div>
							<form class="form" :action="gourl" method="post">
								<input type="" v-show="move" name="LoanJsonList" id="" :value="encold" />
								<input type="" v-show="move" name="PlatformMoneymoremore" id="" :value="p"/>
								<input type="" v-show="move" name="TransferAction" id="" value="1"/>
								<input type="" v-show="move" name="Action" id="" value="1"/>
								<input type="" v-show="move" name="TransferType" id="" value="2"/>
								<input type="" v-show="move" name="ReturnURL" id="IdentificationNo" :value="returnurl" />
								<input type="" v-show="move" name="NotifyURL" id="" :value="resul"/>
								<input type="" v-show="move" name="SignInfo" id="SignInfo" :value="Notifysurl"/>
								<input class="btnzf" type="button" @click.stop="btnzfs(item,index)"  :value="item.prompts_message.button"/>
							</form>
						</div>
					</li>
				</ul>
			</div>
			<!--预投中-->
			<div v-else-if="indexid==1">
				<div class="indexboxbaber">
					<div>项目名称</div>
					<div>预投金额</div>
					<div>投资期限</div>
					<div>回款方式</div>
					<div>投资日期</div>
					<div>年利率</div>
					<div>预计发标时间</div>
					<div>操作</div>
				</div>
				<ul class="indexboxu">
          <li class="indexboxli indexboxbaber3" v-for="(item,index) in datatwo" @click="dataonebtntwo(item)">
						<div class="itemdiv">{{item.name}}</div>
						<div>{{item.amount}}元</div>
						<div>{{item.issue_count}}</div>
						<div>{{item.repay_type_display}}</div>
						<div>{{item.time.split(' ')[0]}}</div>
						<div>{{item.rate}}%</div>
						<div>{{item.kaibiao_date.split(" ")[0]}}</div>
						<div>{{item.prompts_message.status_pc}}</div>
					</li>
				</ul>
			</div>
			<!--已撤销-->
			<div v-else-if="indexid==2">
				<div class="indexboxbaber indexboxbaber3">
					<div>项目名称</div>
					<div>预投金额</div>
					<div>投资期限</div>
					<div>回款方式</div>
					<div>投资日期</div>
					<div>年利率</div>
					<div>状态</div>
				</div>
				<ul class="indexboxu">
          <li class="indexboxli indexboxbaber3" v-for="(item,index) in datathree" @click="dataonebtntwo(item)">
						<div class="itemdiv">{{item.name}}</div>
						<div>{{item.amount}}元</div>
						<div>{{item.issue_count}}</div>
						<div>{{item.repay_type_display}}</div>
						<div>{{item.time.split(' ')[0]}}</div>
						<div>{{item.rate}}%</div>
						<div>{{item.prompts_message.status_pc}}</div>
					</li>
				</ul>
			</div>
			<!--预投成功-->
			<div v-else-if="indexid==3">
				<div class="indexboxbaber indexboxbaber3">
					<div>项目名称</div>
					<div>预投金额</div>
					<div>投资期限</div>
					<div>回款方式</div>
					<div>投资日期</div>
					<div>年利率</div>
					<div>状态</div>
				</div>
				<ul class="indexboxu">
          <li class="indexboxli indexboxbaber3" v-for="(item,index) in datafour" @click="dataonebtntwo(item)">
						<div>{{item.name}}</div>
						<div>{{item.amount}}元</div>
						<div>{{item.issue_count}}</div>
						<div>{{item.repay_type.desc}}</div>
						<div>{{item.time.split(" ")[0]}}</div>
						<div>{{item.rate}}%</div>
						<div>预投成功</div>
					</li>
				</ul>
			</div>
			
			<!--预投失败-->
			<div v-else>
				<div class="indexboxbaber indexboxbaber3">
					<div>项目名称</div>
					<div>预投金额</div>
					<div>投资期限</div>
					<div>回款方式</div>
					<div>投资日期</div>
					<div>年利率</div>
					<div>状态</div>
				</div>
				<ul class="indexboxu">
          <li class="indexboxli indexboxbaber3" v-for="(item,index) in datafive" @click="dataonebtntwo(item)">
						<div>{{item.name}}</div>
						<div>{{item.amount}}元</div>
						<div>{{item.issue_count}}</div>
						<div>{{item.repay_type.desc}}</div>
						<div>{{item.time.split(" ")[0]}}</div>
						<div>{{item.rate}}%</div>
						<div><div style="background-color:#CCCCCC;">预投成功</div></div>
					</li>
				</ul>
			</div>
		</div>
		
		
		
		<div id="indexmoneydiv_1" style="margin-top:20px;">
			我的投资
		</div>
		<div id="indexmoneydiv">
			<div v-for="(item,index) in listtwo" @click="indexidtwo=index" :class="{moveclass:indexidtwo==index}">{{item}}</div>			
		</div>
		<div id="indexmoneybox">

			<!--代还款-->
			<div v-if="indexidtwo==0">
				<div class="indexboxbaber">
					<div>项目名称</div>
					<div>投资金额</div>
					<div>投资期限</div>
					<div>回款方式</div>
					<div>预计投资收益</div>
					<div>年利率</div>
					<div>满标期限</div>
					<div>操作</div>
				</div>
				<ul class="indexboxul">
          <li class="indexboxli" v-for="(item,index) in datalistone" @click="dataonebtn(item)">
					<!-- <router-link class="indexboxli" @click.native="dataonebtn(item)" tag="li" :to="{path:'/borrowmoneydetails/', query: {id:item.id+' 我的投资'}}" v-for="(item,index) in datalistone"> -->
						<div class="itemdiv">{{item.name}}</div>
						<div>{{item.amount}}元</div>
						<div>{{item.issue_count}}</div>
						<div class="itemdiv">{{item.repay_type_display}}</div>
						<div>{{item.interest_income}}元</div>
						<div>{{item.rate}}%</div>
						<div>{{item.limit_date}}</div>
						<div>
							<form class="form" :action="gourl" method="post">
								<input type="" v-show="move" name="LoanJsonList" id="" :value="encold" />
								<input type="" v-show="move" name="PlatformMoneymoremore" id="" :value="p"/>
								<input type="" v-show="move" name="TransferAction" id="" value="1"/>
								<input type="" v-show="move" name="Action" id="" value="1"/>
								<input type="" v-show="move" name="TransferType" id="" value="2"/>
								<input type="" v-show="move" name="ReturnURL" id="IdentificationNo" :value="returnurl" />
								<input type="" v-show="move" name="NotifyURL" id="" :value="resul"/>
								<input type="" v-show="move" name="SignInfo" id="SignInfo" :value="Notifysurl"/>
								<input class="btnzf" type="button" @click.stop="btnzfs(item,index)"  :value="item.prompts_message.button"/>
							</form>
						</div>
					<!-- </router-link> -->
          </li>
				</ul>
			</div>
			<!--回款中-->
			<div v-else-if="indexidtwo==1">
				<div class="indexboxbaber indedxboxbaers" >
					<div>项目名称</div>
					<div>投资金额</div>
					<div>投资期限</div>
					<div>回款方式</div>
					<div>投资日期</div>
					<div>年利率</div>
					<div>已回本金</div>
					<div>状态</div>
					<div style="color:#333333;">操作</div>
				</div>
				<ul class="indexboxu">
          <li class="indexboxli indedxboxbaers" v-for="(item,index) in datalisttwo" @click="dataonebtn(item)">
						<div class="itemdiv">{{item.name}}</div>
						<div>{{item.amount}}元</div>
						<div>{{item.issue_count}}</div>
						<div class="itemdiv">{{item.repay_type_display}}</div>
						<div>{{item.time.split(" ")[0]}}</div>
						<div>{{item.rate}}%</div>
						<div>{{item.payback_capital}}元</div>
						<div>{{item.prompts_message.msg}}</div>
						<div @click.stop="pdfTest(item)">借款合同</div>
					</li>
				</ul>
			</div>
			<!--投资待满标-->
			<div v-else-if="indexidtwo==2">
				<div class="indexboxbaber">
					<div>项目名称</div>
					<div>投资金额</div>
					<div>投资期限</div>
					<div>回款方式</div>
					<div>预计投资收益</div>
					<div>年利率</div>				
					<div>投资进度</div>
          <div>满标期限</div>
				</div>
				<ul class="indexboxul">
          <li class="indexboxli" v-for="(item,index) in datalistthree" @click="dataonebtn(item)">
						<div class="itemdiv">{{item.name}}</div>
						<div>{{item.amount}}元</div>
						<div>{{item.issue_count}}</div>
						<div class="itemdiv">{{item.repay_type_display}}</div>
						<div>{{item.interest_income}}元</div>
						<div>{{item.rate}}%</div>
            <div>{{item.progress}}%</div>		
            <div>{{item.limit_date}}</div>						
					</li>
				</ul>
			</div>
			<!--款已回清-->
			<div v-else-if="indexidtwo==3">
				<div class="indexboxbaber">
					<div>项目名称</div>
					<div>投资金额</div>
					<div>投资期限</div>
					<div>回款方式</div>
					<div>投资收益</div>
					<div>年利率</div>
					<div>满标期限</div>
					<div>状态</div>
				</div>
				<ul class="indexboxul">
          <li class="indexboxli" v-for="(item,index) in datalistfive" @click="dataonebtn(item)">
						<div class="itemdiv">{{item.name}}</div>
						<div>{{item.amount}}元</div>
						<div>{{item.issue_count}}</div>
						<div class="itemdiv">{{item.repay_type_display}}</div>
						<div>{{item.interest_income}}元</div>
						<div>{{item.rate}}%</div>
						<div>{{item.limit_date}}</div>
						<div><div>{{item.prompts_message.status_pc}}</div></div>
					</li>
				</ul>
			</div>
			<!--债转中-->
			<div v-else-if="indexidtwo==4">
				<div class="indexboxbaber">
					<div>项目名称</div>
					<div>投资金额</div>
					<div>投资期限</div>
					<div>回款方式</div>
					<div>投资收益</div>
					<div>年利率</div>
					<div>债转本金</div>
					<div>操作</div>
				</div>
				<ul class="indexboxul">
          <li class="indexboxli" v-for="(item,index) in datalistsex" @click="dataonebtn(item)">
						<div class="itemdiv">{{item.name}}</div>
						<div>{{item.amount}}元</div>
						<div>{{item.issue_count}}</div>
						<div class="itemdiv">{{item.repay_type_display}}</div>
						<div>{{item.interest_income}}元</div>
						<div>{{item.rate}}%</div>
						<div>{{item.investment_transfer_amount}}</div>
						<div><div>{{item.prompts_message.button}}</div></div>
					</li>
				</ul>
			</div>
			<!--已债转-->
			<div v-else-if="indexidtwo==5">
				<div class="indexboxbaber">
					<div>项目名称</div>
					<div>投资金额</div>
					<div>投资期限</div>
					<div>回款方式</div>
					<div>投资收益</div>
					<div>年利率</div>
					<div>债转本金</div>
					<div>状态</div>
				</div>
				<ul class="indexboxul">
          <li class="indexboxli" v-for="(item,index) in datalista" @click="dataonebtn(item)">
					
						<div class="itemdiv">{{item.name}}</div>
						<div>{{item.amount}}元</div>
						<div>{{item.issue_count}}</div>
						<div class="itemdiv">{{item.repay_type_display}}</div>
						<div>{{item.interest_income}}元</div>
						<div>{{item.rate}}%</div>
						<div>{{item.investment_transfer_amount}}</div>
						<div><div style="background-color:#CCCCCC;">{{item.prompts_message.status_pc}}</div></div>
					</li>
				</ul>
			</div>
			<!--已撤销-->
			<div v-else-if="indexidtwo==6">
				<div class="indexboxbaber">
					<div>项目名称</div>
					<div>投资金额</div>
					<div>投资期限</div>
					<div>回款方式</div>
					<div>预计投资收益</div>
					<div>年利率</div>
					<div>满标期限</div>
					<div>状态</div>
				</div>
				<ul class="indexboxul">
           <li class="indexboxli" v-for="(item,index) in datalistb" @click="dataonebtn(item)">
				
						<div class="itemdiv">{{item.name}}</div>
						<div>{{item.amount}}元</div>
						<div>{{item.issue_count}}</div>
						<div class="itemdiv">{{item.repay_type_display}}</div>
						<div>{{item.interest_income}}元</div>
						<div>{{item.rate}}%</div>
						<div>{{item.limit_date}}</div>
						<div>{{item.prompts_message.status_pc}}</div>
					</li>
				</ul>
			</div>
			<!--投资失败-->
			<div v-else>
				<div class="indexboxbaber">
					<div>项目名称</div>
					<div>投资金额</div>
					<div>投资期限</div>
					<div>回款方式</div>
					<div>预计投资收益</div>
					<div>年利率</div>
					<div>满标期限</div>
					<div>投资失败原因</div>
				</div>
				<ul class="indexboxul">
          <li class="indexboxli" v-for="(item,index) in datalistc" @click="dataonebtn(item)">
						<div class="itemdiv">{{item.name}}</div>
						<div>{{item.amount}}元</div>
						<div>{{item.issue_count}}</div>
						<div class="itemdiv">{{item.repay_type_display}}</div>
						<div>{{item.interest_income}}元</div>
						<div>{{item.rate}}%</div>
						<div>{{item.limit_date}}</div>
						<div>{{item.prompts_message.msg}}</div>
					</li>
				</ul>
			</div>
		</div>
	</div>
</template>

<script>
export default {
  data() {
    return {
      contractbtn: "", //合同点击按钮
      contract: "", //借款合同内容
      imgs: require("../../imgs/mine/gongsizhang.png"),
      imgsbas64: "", //bes64图片
      gourl: "", //乾多多待支付
      move: false,
      my_data: "", //我的个人资料
      LoanJsonList: [], //转账列表没有encode
      encold: [], //转账列表encode过的
      Notifysurl: "", //秘钥
      token: window.sessionStorage.token, //token
      list: ["待支付", "预投中", "已撤销", "预投成功", "预投失败"],
      listtwo: [
        "待支付",
        "回款中",
        "投资待满标",
        "款已回清",
        "债转中",
        "已债转",
        "已撤销",
        "投资失败"
      ],
      indexid: 0,
      indexidtwo: 0,
      value1: "",
      value2: "",
      selects: "",
      date1: "",
      date2: "",
      dataall: "", // 全局数据
      dataone: [], //预投的待支付
      datatwo: [], //预投的预投中
      datathree: [], //预投的已撤销
      datafour: [], //获取到的我的预投数据的预投成功
      datafive: [], //预投的预投失败,

      datalistone: [], //投资待支付
      datalisttwo: [], //投资回款中
      datalistthree: [], //投资投资待满标
      datalistfive: [], //投资回款方式
      datalistsex: [], //投资债转中
      datalista: [], //投资已债转
      datalistb: [], //投资已撤销
      datalistc: [], //投资的投资失败

      p: window.sessionStorage.p, //乾多多平台标识
      resul: "", //后台通知网址
      returnurl: "", //前端通知网址
      investment_statistics: "" //投资统计
    };
  },
  created() {
    this.gourl = this.$url.MONEYNFIVE;
    this.returnurl = this.$url.URL + this.$url.PAYRETURN;
    this._getData();
    this._myindexdata(); //获取我的个人资料
    this._getdataone();
    this.dataall = JSON.parse(window.sessionStorage.dataall);

    //实现将项目的图片转化成base64
    function convertImgToBase64(url, callback, outputFormat) {
      var canvas = document.createElement("CANVAS"),
        ctx = canvas.getContext("2d"),
        img = new Image();
      img.crossOrigin = "Anonymous";
      img.onload = function() {
        canvas.height = img.height;
        canvas.width = img.width;
        ctx.drawImage(img, 0, 0);
        var dataURL = canvas.toDataURL(outputFormat || "image/png");
        callback.call(this, dataURL);
        canvas = null;
      };
      img.src = url;
    }
    convertImgToBase64(this.imgs, base64Img => {
      this.imgsbas64 = base64Img;
    });

    this.resul =
      this.$url.QIANDUODUO +
      JSON.parse(window.sessionStorage.dataall).TRANSFER_CALLBACK; //转账后台接口

    //获取投资统计数据
    // this.$http
    //   .get(this.$url.URL + this.$url.INVESTMENT_STATISTICS, {
    //     headers: {
    //       Authorization: "JWT " + this.token
    //     }
    //   })
    //   .then(response => {
    //     this.investment_statistics = response.data;
    //   });
  },
  methods: {
    repealbtn(item) {
      this.$http
        .post(
          this.$url.URL + this.$url.CANCEL_INVEST,
          {
            investment_id: item.id
          }
        )
        .then(response => {
          if (response.data.code == "0") {
            this.dataone = []; //预投的待支付
            this.datatwo = []; //预投的预投中
            this.datathree = []; //预投的已撤销
            this.datafour = []; //获取到的我的预投数据的预投成功
            this.datafive = []; //预投的预投失败,

            this.datalistone = []; //投资待支付
            this.datalisttwo = []; //投资回款中
            this.datalistthree = []; //投资投资待满标
            this.datalistfive = []; //投资回款方式
            this.datalistsex = []; //投资债转中
            this.datalista = []; //投资已债转
            this.datalistb = []; //投资已撤销
            this.datalistc = [];
            this._getData();
            this._getdataone();
          }
        });
    },
    dataonebtn(item){
      //我的预投
      window.sessionStorage.dataitemone = JSON.stringify(item);
      this.$router.push({path:'/borrowmoneydetails/', query: {id:item.id+' 我的投资'}})
    },
    dataonebtntwo(item){
      window.sessionStorage.dataitemone = JSON.stringify(item);
      this.$router.push({path:'/borrowmoneydetails/', query: {id:item.id+' 我的预投'}})
    },
    indexidbtn(index) {
      this.indexid = index;
    },
    _getData() {
      this.$http
        .get(this.$url.URL + this.$url.MY_PRE_INVESTMENT)
        .then(response => {
          var data = response.data.results;
          for (let i = 0; i < data.length; i++) {
            if (data[i].issue_type == "MONTH") {
              data[i].issue_count = data[i].issue_count + "个月";
            } else {
              data[i].issue_count = data[i].issue_count + "天";
            }
            if (
              data[i].prompts_message.status_pc == "预投成功" &&
              data[i].progress == 100
            ) {
              this.datafour.push(data[i]);
              for (let l = 0; l < this.datafour.length; l++) {
                for (let s = 0; s < this.dataall.repay_type.length; s++) {
                  if (
                    this.datafour[l].repay_type ==
                    this.dataall.repay_type[s].code
                  ) {
                    this.datafour[l].repay_type = this.dataall.repay_type[s];
                  }
                }
              }
            } else if (data[i].prompts_message.status_pc == "待支付") {
              this.dataone.push(data[i]);
              for (let l = 0; l < this.dataone.length; l++) {
                for (let s = 0; s < this.dataall.repay_type.length; s++) {
                  if (
                    this.dataone[l].repay_type ==
                    this.dataall.repay_type[s].code
                  ) {
                    this.dataone[l].repay_type = this.dataall.repay_type[s];
                  }
                }
              }
            } else if (
              data[i].prompts_message.status_pc == "预投成功" &&
              data[i].progress < 100
            ) {
              this.datatwo.push(data[i]);
              for (let l = 0; l < this.datatwo.length; l++) {
                for (let s = 0; s < this.dataall.repay_type.length; s++) {
                  if (
                    this.datatwo[l].repay_type ==
                    this.dataall.repay_type[s].code
                  ) {
                    this.datatwo[l].repay_type = this.dataall.repay_type[s];
                  }
                }
              }
            } else if (data[i].prompts_message.status_pc == "已撤销") {
              this.datathree.push(data[i]);
              for (let l = 0; l < this.datathree.length; l++) {
                for (let s = 0; s < this.dataall.repay_type.length; s++) {
                  if (
                    this.datathree[l].repay_type ==
                    this.dataall.repay_type[s].code
                  ) {
                    this.datathree[l].repay_type = this.dataall.repay_type[s];
                  }
                }
              }
            } else if (data[i].prompts_message.status_pc == "预投失败") {
              this.datafive.push(data[i]);
              for (let l = 0; l < this.datafive.length; l++) {
                for (let s = 0; s < this.dataall.repay_type.length; s++) {
                  if (
                    this.datafive[l].repay_type ==
                    this.dataall.repay_type[s].code
                  ) {
                    this.datafive[l].repay_type = this.dataall.repay_type[s];
                  }
                }
              }
            }
          }
        });
    },
    _getdataone() {
      this.$http
        .get(this.$url.URL + this.$url.MY_INVESTMENT) //我的投资数据
        .then(response => {
          var dataone = response.data.results;
          for (let i = 0; i < dataone.length; i++) {
            if (dataone[i].issue_type == "MONTH") {
              dataone[i].issue_count = dataone[i].issue_count + "个月";
            } else {
              dataone[i].issue_count = dataone[i].issue_count + "天";
            }
            if (dataone[i].prompts_message.status_pc == "待支付") {
              this.datalistone.push(dataone[i]);
            } else if (
              dataone[i].prompts_message.status_pc == "回款中" &&
              dataone[i].progress == "100"
            ) {
              this.datalisttwo.push(dataone[i]);
            } else if (
              dataone[i].prompts_message.status_pc == "回款中" &&
              dataone[i].progress < 100
            ) {
              this.datalistthree.push(dataone[i]);
            } else if (dataone[i].prompts_message.status_pc == "款已回清") {
              this.datalistfive.push(dataone[i]);
            } else if (dataone[i].prompts_message.status_pc == "债转中") {
              this.datalistsex.push(dataone[i]);
            } else if (dataone[i].prompts_message.status_pc == "已债转") {
              this.datalista.push(dataone[i]);
            } else if (dataone[i].prompts_message.status_pc == "已撤销") {
              this.datalistb.push(dataone[i]);
            } else if (dataone[i].prompts_message.status_pc == "投资失败") {
              this.datalistc.push(dataone[i]);
            }
          }
        });
    },
    _myindexdata() {
      //获取我的个人数据

      this.$http
        .get(this.$url.URL + this.$url.MY_INDEX_DATA)
        .then(response => {
          this.my_data = response.data;
          window.sessionStorage.myindexdata = JSON.stringify(response.data);
        });
    },
    btnzfs(item, index) {
      let id = item.id;

      this.LoanJsonList = []; //点击前先让转账列表变为空
      if (Number(item.amount) <= Number(this.my_data.available_remain)) {
        this.$http
          .post(
            this.$url.URL + this.$url.PAY_INVEST,
            {
              investment_id: id
            }
          )
          .then(response => {
            let list = response.data.LoanJsonList;
            if (list !== undefined) {
              for (let i = 0; i < list.length; i++) {
                if (list[i].SecondaryJsonList.length > 0) {
                  list[i].SecondaryJsonList = JSON.stringify(
                    list[i].SecondaryJsonList
                  );
                } else {
                  delete list[i].SecondaryJsonList;
                }

                this.LoanJsonList.push(list[i]);
              }
              this.LoanJsonList = JSON.stringify(this.LoanJsonList);
              this.$http
                .post(this.$url.URL + this.$url.ENCODEURL, {
                  data: this.LoanJsonList
                })
                .then(response => {
                  this.encold = response.data.data;
                });

              let str =
                this.LoanJsonList +
                this.p +
                "112" +
                this.returnurl +
                this.resul;
              this.$http
                .post(this.$url.URL + this.$url.SIGNATURE, {
                  //获取秘钥接口
                  str: str
                })
                .then(response => {
                  this.Notifysurl = response.data.result;
                  this.$confirm("是否前往乾多多支付页面?", "提示", {
                    confirmButtonText: "确定",
                    cancelButtonText: "取消",
                    type: "warning"
                  })
                    .then(() => {
                      var forms = document.querySelectorAll(".form");
                      forms[index].submit();
                    })
                    .catch(() => {});
                });
            } else {
              this.$alert(response.data.msg);
            }
          });
      } else {
        this.$confirm("账户余额不够是否前往充值", "提示", {
          confirmButtonText: "确定",
          cancelButtonText: "取消",
          type: "warning"
        })
          .then(() => {
            this.$router.push("/indexrecharge");
          })
          .catch(() => {});
      }
    },
    _contract(item) {
      this.$http
        .get(this.$url.URL + this.$url.CONTRACT + "/" + item.id + "/")
        .then(response => {
          if (response.status == "200") {
            this.contract = response.data;
            this.contractbtn = true;
            conosle.log("aaaaa");
          } else {
            this.contractbtn = false;
            this.$alert("还未放款未生成合同");
          }
        })
        .catch(() => {});
    },
    pdfTest(item) {
      this._queryscontrect(item);
    },
    _queryscontrect(item){
      this.$http.post(this.$url.URL+this.$url.CONTRACT_INVESTMENT,{
        investment_id:item.id
      })
      .then(res=>{
        window.open(res.data.url)
      })
    },
  },
  watch: {
    value1: function() {
      if (this.value1 == "") {
        this.value2 = "";
      }
    },
    value2: function() {}
  },
  mounted() {
    var set = setInterval(() => {
      if (this.$route.name == "indexstatistics") {
        var h = $(".indexmoney").height();
        var hs = 0;
        if (h > 760) {
          hs = h + 150 + 400 + 20;
        } else {
          hs = 760 + 150 + 400 + 20;
        }
        $("html").height(hs);
        $("body").height(hs);
      } else {
        clearInterval(set);
      }
    }, 100);
  }
};
</script>

<style scoped="scoped">
@import "../../../static/css/homecss/indexmoney.css";
#indexmoneydiv_1 {
  height: 60px;
  font-size: 18px;
  color: #fd8f01;
  line-height: 60px;
  font-weight: bold;
  background-color: #ffffff;
  text-indent: 20px;
}
#indexmoneydiv {
  margin: 0 !important;
}
.indexboxbaber2 > div:nth-of-type(1) {
  width: 125px;
  overflow: hidden; /*超出部分隐藏*/
  white-space: nowrap; /*不换行*/
  text-overflow: ellipsis; /*超出部分文字以...显示*/
}
.indexboxbaber3 > div {
  width: 14.2857%;
  overflow: hidden; /*超出部分隐藏*/
  white-space: nowrap; /*不换行*/
  text-overflow: ellipsis; /*超出部分文字以...显示*/
}
.itemdiv {
  width: 12.5%;
  text-overflow: ellipsis;
  overflow: hidden;
  white-space: nowrap;
}
.indexboxli > div {
  height: 100%;
  overflow: hidden; /*超出部分隐藏*/
  white-space: nowrap; /*不换行*/
  text-overflow: ellipsis; /*超出部分文字以...显示*/
}
.btnzf {
  border: none;
  width: 100px;
  height: 30px;
  outline: none;
  border-radius: 6px;
  background-color: #fd8f00;
  color: #ffffff;
  cursor: pointer;
}
.indedxboxbaers > div {
  width: 11.111111%;
}
.indedxboxbaers > div:nth-of-type(9) {
  color: #2f81fd;
}
</style>