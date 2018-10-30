<template>
	<div class="indexmoney">
		<!-- <ul class="indexmoneyul">
			<li id="indexoneli">借款统计</li>
			<li>
				<div>借款总额</div>
				<div>待还总额</div>
				<div>待还本金</div>
				<div>待还利息</div>
				<div>待还罚息</div>
			</li>
			<li>
				<div>￥{{this.borrow_statistics.loan_summary}}</div>
				<div>￥{{this.borrow_statistics.no_repay_summary}}</div>
				<div>￥{{this.borrow_statistics.no_repay_capital}}</div>
				<div>￥{{this.borrow_statistics.no_repay_interest}}</div>
				<div>￥{{this.borrow_statistics.no_repay_fine}}</div>
			</li>
		</ul> -->
		<div style="width:100%;height:60px;font-size:18px;font-weight:bold;text-indent: 20px;color:#FD8F01; line-height: 60px;background:#FFFFFF;">我的借款</div>
		<div id="indexmoneydiv" style="margin-top:0;">
			<div v-for="(item,index) in list" @click="indexidbtn(index)" :class="{moveclass:indexid==index}">{{item}}</div>			
		</div>
		<div id="indexmoneybox">
			
			<!--代还款-->
			<div v-if="indexid==0">
				<div class="indexboxbaber indexonebaber">
					<div>项目名称</div>
					<div>借款金额</div>
					<div>借款期限</div>
					<div>还款方式</div>
					<div>还款期数</div>
					<div>应还金额</div>
					<div>最迟还款日</div>
					<div>合同</div>
          <div>操作</div>
				</div>
				<ul class="indexboxul">
					<li @click="routerbtn(item,index)" class="indexboxli indexonebaber" v-for="(item,index) in listone">
						<div style="width:12.5%">{{item.name}}</div>
						<div>{{item.amount}}元</div>
						<div>{{item.issue_count}}</div>
						<div>{{item.repay_type_display}}</div>
						<div>第{{item.prompts_message.msg.last_payment_num}}期</div>
						<div>{{item.prompts_message.msg.last_payment_amount}} 元</div>
						<div>{{item.prompts_message.msg.last_payment_day}}</div>
            <div @click.stop="contractbtn(item)" style="color:#2F81FD;">借款合同</div>
						<div>
							<div @click.stop="btn_hk(item,index)">还款</div>
						</div>
            
					</li>
				</ul>
			</div>
			<!--审核中-->
			<div v-else-if="indexid==1">
				<div class="indexboxbaber">
					<div>项目名称</div>
					<div>借款金额</div>
					<div>借款期限</div>
					<div>还款方式</div>
					<div>借款时间</div>
					<div>满标期限</div>
					<div>状态</div>
					<div>操作</div>
				</div>
				<ul class="indexboxu">
					<li  class="indexboxli indexboxlis" v-for="item in listtwo">
						<div style="width:12.5%">{{item.name}}</div>
						<div>{{item.amount}}元</div>
						<div>{{item.issue_count}}</div>
						<div>{{item.repay_type_display}}</div>
						<div>{{item.date.split(" ")[0]}}</div>
						<div v-if="item.limit!==null">{{item.limit}}</div>
            <div v-else>待审核</div>
						<div>{{item.prompts_message.msg}}</div>
						<div><div @click.stop="repealbtn(item)">{{item.prompts_message.button}}</div></div>
					</li>
				</ul>
			</div>
			<!--招标中-->
			<div v-else-if="indexid==2">
				<div  class="indexboxbaber indexboxbaber1">
					<div style="width:14.28571428571428%">项目名称</div>
					<div>借款金额</div>
					<div>借款期限</div>
					<div>还款方式</div>
					<div>借款时间</div>
					<div>招标进度</div>
					<div>状态</div>
				</div>
				<ul class="indexboxu">
					<li @click="routerbtn(item)" class="indexboxli indexboxbaber1" v-for="item in listthree">
						<div style="width:14.28571428571428%" >{{item.name}}</div>
						<div>{{item.amount}}元</div>
						<div>{{item.issue_count}}</div>
						<div>{{item.repay_type_display}}</div>
						<div>{{item.date.split(" ")[0]}}</div>
						<div>已招标{{item.progress}}%</div>
						<div>{{item.prompts_message.msg}}</div>
					</li>
				</ul>
			</div>
			<!--已还清-->
			<div v-else-if="indexid==3">
				<div class="indexboxbaber indexboxbaber2">
					<div>项目名称</div>
					<div>招标金额</div>
					<div>招标期限</div>
					<div>还款方式</div>
					<div>借款时间</div>
					<div>状态</div>
				</div>
				<ul class="indexboxu">
					<li @click="routerbtn(item)" class="indexboxli indexboxbaber3" v-for="item in listfour">
						<div>{{item.name}}</div>
						<div>{{item.amount}}元</div>
						<div>{{item.issue_count}}</div>
						<div>{{item.repay_type_display}}</div>
						<div>{{item.date.split(" ")[0]}}</div>
						<div>{{item.prompts_message.msg}}</div>
					</li>
				</ul>
			</div>
			<!--已撤销-->
			<div v-else-if="indexid==4">
				<div class="indexboxbaber indexboxbaber2">
					<div>项目名称</div>
					<div>招标金额</div>
					<div>招标期限</div>
					<div>还款方式</div>
					<div>借款时间</div>
					<div>状态</div>
				</div>
				<ul class="indexboxu">
					<li class="indexboxli indexboxbaber3" v-for="item in listfive">
						<div>{{item.name}}</div>
						<div>{{item.amount}}元</div>
						<div>{{item.issue_count}}</div>
						<div>{{item.repay_type_display}}</div>
						<div>{{item.date.split(" ")[0]}}</div>
						<div>{{item.prompts_message.msg}}</div>
					</li>
				</ul>
			</div>
			<!--借款失败-->
			<div v-else>
				<div class="indexboxbaber indexboxbaber2">
					<div>项目名称</div>
					<div>招标金额</div>
					<div>招标期限</div>
					<div>还款方式</div>
					<div>借款时间</div>
					<div>失败原因</div>
				</div>
				<ul class="indexboxu">
					<li @click="routerbtn(item)" class="indexboxli indexboxbaber3" v-for="item in listsix">
						<div>{{item.name}}</div>
						<div>{{item.amount}}元</div>
						<div>{{item.issue_count}}</div>
						<div>{{item.repay_type_display}}</div>
						<div>{{item.date.split(" ")[0]}}</div>
						<div><div>{{item.prompts_message.msg}}</div></div>
					</li>
				</ul>
			</div>
			
		</div>
    <div v-show="movelist" id="movelistid" >
      <div>
        <div id="titlename">合同列表
          <img src="../../imgs/mine/hetongguanbi.png" alt="" @click.stop="movelist=false">
        </div>
        <div id="titlebox">
            <div v-for="item in listhetong" @click="gohetong(item)" class="titleboxs">
              <div class="titleboxsdiv">
                  <br>
                  出借人
                  <div style="margin-top:10px;">{{item.investment_real_name}}</div>
                  <div style="margin-top:10px;">出借金额</div>
                  <div style="margin-top:10px;">{{item.amount}}元</div>

              </div>
            </div>
        </div>
      </div>
    </div>
	</div>
</template>

<script>
// import "../../../static/js/pdfmake/pdfmake.js";
// import "../../../static/js/pdfmake/vfs_fonts.js";
export default {
  data() {
    return {
      movelist:false,
      list: ["待还款", "审核中", "招标中", "已还清", "已撤销", "借款失败"],
      imgs:require('../../imgs/mine/gongsizhang.png'),
      listhetong:"",//合同
      indexid: 0,
      value1: "",
      value2: "",
      selects: "",
      date1: "",
      date2: "",
      lists: "", //列表
      listone: [], //1
      listtwo: [], //2
      listthree: [], //3
      listfour: [], //4
      listfive: [], //5
      listsix: [], //6
      borrow_statistics: "", //借款统计
      token: window.sessionStorage.token
    };
  },
  created() {
    //图片转bes64
    function convertImgToBase64(url, callback, outputFormat){
      var canvas = document.createElement('CANVAS'),
        ctx = canvas.getContext('2d'),
        img = new Image;
      img.crossOrigin = 'Anonymous';
      img.onload = function(){
        canvas.height = img.height;
        canvas.width = img.width;
        ctx.drawImage(img,0,0);
        var dataURL = canvas.toDataURL(outputFormat || 'image/png');
        callback.call(this, dataURL);
        canvas = null; 
      };
      img.src = url;
    }
    convertImgToBase64(this.imgs,(base64Img)=>{
      this.imgsbas64=base64Img
    });     



    var token = window.sessionStorage.token;
    this.$http
      .get(this.$url.URL + this.$url.MY_LOAN)
      .then(response => {
        for (let i = 0; i < response.data.results.length; i++) {
          if (response.data.results[i].project !== null) {
            response.data.results[i].project.limit =
              response.data.results[i].limit_data;
            response.data.results[i] = response.data.results[i].project;
          }
        }
        this.lists = response.data.results;
        for (let i = 0; i < this.lists.length; i++) {
          if (this.lists[i].issue_type == "MONTH") {
            if (this.lists[i].limit == undefined) {
              this.lists[i].limit = this.lists[i].limit_date;
              this.lists[i].limit = this.lists[i].limit;
            } else {
              this.lists[i].limit = this.lists[i].limit + "个月";
            }
            this.lists[i].issue_count = this.lists[i].issue_count + "个月";
          } else {
            this.lists[i].issue_count = this.lists[i].issue_count + "天";
            this.lists[i].limit = this.lists[i].limit + "天";
          }
          if (this.lists[i].pc_status == "待还款") {
            this.listone.push(this.lists[i]);
          } else if (this.lists[i].pc_status == "审核中") {
            this.listtwo.push(this.lists[i]);           
          } else if (this.lists[i].pc_status == "招标中") {
            this.listthree.push(this.lists[i]);
          } else if (this.lists[i].pc_status == "已还清") {
            this.listfour.push(this.lists[i]);
          } else if (this.lists[i].pc_status == "已撤销") {
            this.listfive.push(this.lists[i]);
          } else if (this.lists[i].pc_status == "借款失败") {
            this.listsix.push(this.lists[i]);
          }
        }
      });
    //获取借款统计数据
    this.$http
      .get(this.$url.URL + this.$url.BORROW_STATISTICS)
      .then(response => {
        this.borrow_statistics = response.data;
      });
  },
  methods: {
    contractbtn(item){
      this.movelist=true
      this.$http.get(this.$url.URL+this.$url.PROJECT_CONTRACT+item.id+"/")
      .then((response)=>{
        this.listhetong=response.data.invested_project
      })
    },
    indexidbtn(index) {
      this.indexid = index;
    },
    gohetong(item){
      this._queryscontrect(item);
      console.log(item)
    },
    _queryscontrect(item){
      this.$http.post(this.$url.URL+this.$url.CONTRACT_INVESTMENT,{
        investment_id:item.id
      })
      .then(res=>{
        window.open(res.data.url)
      })
    },
    routerbtn(item) {
      if (item.prompts_message !== undefined) {
        window.sessionStorage.jklist = JSON.stringify(item);
        this.$router.push({
          path: "/borrowmonydatailsa"
        });
      }
    },
    btn_hk(item) {
      window.sessionStorage.borrowmoney = JSON.stringify(item);
      this.$router.push("/indexrefund");
    },
    repealbtn(item) {
      if(item.prompts_message.button=="撤销"){
      var types = "";
      if (item.project === undefined) {
        types = "PROJECT";
      } else {
        types = "LOAN_APPLY";
      }
      this.$http
        .post(
          this.$url.URL + this.$url.CANCEL_LOAN,
          {
            id: item.id,
            type: types
          }
        )
        .then(response => {
          if (response.data.code == "0") {
            this.$http
              .get(this.$url.URL + this.$url.MY_LOAN)
              .then(response => {
                for (let i = 0; i < response.data.results.length; i++) {
                  if (response.data.results[i].project !== null) {
                    response.data.results[i] = response.data.results[i].project;
                  }
                }
                this.lists = response.data.results;
                this.listone = [];
                this.listtwo = [];
                this.listthree = [];
                this.listfour = [];
                this.listfive = [];
                this.listsix = [];
                for (let i = 0; i < this.lists.length; i++) {
                  if (this.lists[i].issue_type == "MONTH") {
                    if (this.lists[i].limit == undefined) {
                      this.lists[i].limit = this.lists[i].limit_date;
                      this.lists[i].limit = this.lists[i].limit;
                    } else {
                      this.lists[i].limit = this.lists[i].limit + "个月";
                    }
                    this.lists[i].issue_count =
                      this.lists[i].issue_count + "个月";
                  } else {
                    this.lists[i].issue_count = this.lists[i].issue_count + "天";
                    this.lists[i].limit = this.lists[i].limit + "天";
                  }
                  if (this.lists[i].pc_status == "待还款") {
                    this.listone.push(this.lists[i]);
                  } else if (this.lists[i].pc_status == "审核中") {
                    this.listtwo.push(this.lists[i]);
                  } else if (this.lists[i].pc_status == "招标中") {
                    this.listthree.push(this.lists[i]);
                  } else if (this.lists[i].pc_status == "已还清") {
                    this.listfour.push(this.lists[i]);
                  } else if (this.lists[i].pc_status == "已撤销") {
                    this.listfive.push(this.lists[i]);
                  } else if (this.lists[i].pc_status == "借款失败") {
                    this.listsix.push(this.lists[i]);
                  }
                }
              });
          } else {
            this.$alert("撤销失败");
          }
        })
      }
     
    },
    repealbtntwo(item) {
      this.$http
        .post(
          this.$url.URL + this.$url.CANCEL_LOAN,
          {
            id: item.id,
            type: "PROJECT"
          }
        )
        .then(response => {
        });
    }
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
      if (this.$route.name == "indexmoney") {
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
    }, 200);
  }
};
</script>

<style scoped="scoped">
@import "../../../static/css/homecss/indexmoney.css";
/* 设置滚动条的样式 */
	    ::-webkit-scrollbar {
	        width: 5px;
	        height: 5px;
	    }
	    /* 滚动槽 */
	    ::-webkit-scrollbar-track {
	        -webkit-box-shadow: inset 0 0 6px rgba(0, 0, 0, 0.3);
	        border-radius: 5px;
	    }
	    /* 滚动条滑块 */
	    ::-webkit-scrollbar-thumb {
	        border-radius: 10px;
	        background: rgba(0, 0, 0, 0.1);
	        -webkit-box-shadow: inset 0 0 6px rgba(0, 0, 0, 0.5);
	    }

.indexboxli > div {
  overflow: hidden; /*超出部分隐藏*/
  white-space: nowrap; /*不换行*/
  text-overflow: ellipsis; /*超出部分文字以...显示*/
}
.indexboxlis > div {
  width: 12.5%;
  overflow: hidden; /*超出部分隐藏*/
  white-space: nowrap; /*不换行*/
  text-overflow: ellipsis; /*超出部分文字以...显示*/
}
.indexboxbaber3 > div {
  width: 16.666666%;
}
.pbtn {
  width: 60%;
  background-color: #dcdcdc;
  margin: auto;
  margin-top: 9px;

  height: 30px;
  line-height: 30px;
  color: #ffffff;
  border-radius: 4px;
}
.indexonebaber>div{
  width:11.11111111% !important;
}
#movelistid{
  width:100%;
  height:100%;
  position: fixed;
  left:0;
  right:0;
  top:0;
  bottom:0;
  background:rgba(0, 0, 0, 0.7);
  z-index: 99999;
}
#movelistid>div{
  width:870px;
  height:480px;
  position:absolute;
  top:50%;
  left:50%;
  margin-left:-435px;
  margin-top:-240px;
  background:#eeeeee;
  border-radius: 10px;
  overflow: hidden;
}
#titlename{
  width:100%;
  height:60px;
  background: #2f81fd;
  font-size:22px;
  text-align: center;
  line-height: 60px;
  color:#ffffff;
}
#titlebox{
  width:100%;
  height:400px;
  overflow-y: scroll;
  margin-top:20px;
}
.titleboxs{
  width:150px;
  height:150px;
  float:left;
  margin:0 10.1px;
  margin-bottom:10px;
  background:url(../../imgs/mine/hetong.png) no-repeat;
  background-size:100% 100%;
  border:1px solid #999999;
  cursor: pointer;
}
.titleboxsdiv{
  width:100%;
  height:100%;
  background:rgba(0, 0, 0, 0.6);
  display:none;
  text-align: center;
  font-size:14px;
  color:#ffffff;
}
.titleboxs:hover .titleboxsdiv{
  display:block;
}
#titlename>img{
  position: absolute;;
  cursor: pointer;
  top:20px;
  right:20px;
}
</style>