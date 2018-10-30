<template>
	<div class="indexbill">
		<div id="indexdataright">
			<div id="indexdatatop">
				<div id="indextext" style="width:90px;">我的体验金</div>
			</div>
		</div>
		<ul id="ul_1">
			<li>
				<div>体验金金额</div>
				<div>{{my_datatyj.amount}}元</div>
			</li>
      <li>
				<div>体验金投资金额</div>
				<div>{{my_datatyj.invest_amount}}元</div>
			</li>
			<li>
				<div>体验金领取日期</div>
				<div>{{my_datatyj.receive_date}}</div>
			</li>
			<li>
				<div>体检金状态</div>
				<div>{{my_datatyj.status_display}}</div>
			</li>
			<li>
				<div>体验金使用日期</div>
				<div>{{my_datatyj.invest_date}} </div>
			</li>
			<li>
				<div>体验金收益</div>
				<div>{{my_datatyj.release_income}}元</div>
			</li>			
		</ul>
    <div class="class_1" :class="{class_2:my_datatyj.status_display=='已完成'}" @click="btn(my_datatyj.status_display)">{{my_datatyj.status_display|vfilter}}</div>
	</div>
</template>

<script>
export default {
  data() {
    return {
      my_datatyj: JSON.parse(window.sessionStorage.myindexdata).experience_money
    };
  },
  created() {
    console.log(JSON.parse(window.sessionStorage.myindexdata).experience_money)
  },
  mounted() {
    var h = $(".indexaward").height();
    var hd = "";
    if (h > 740) {
      hd = h;
    } else {
      hd = 740;
    }
    var hs = hd + 190 + 400;
    $("html").height(hs);
    $("body").height(hs);
  },
  filters: {
    vfilter(val) {
      if (val == "未使用") {
        return "立即体验";
      } else {
        return "查看投资详情";
      }
    }
  },
  methods: {
    btn(item) {
      if (item == "未使用") {
        this.$store.state.investonehomeindex = "4";
        this.$router.push("/investonehome");
      }else if(item=="使用中"){
        this.$router.push("/indexstatistics")
      }else{

      }
    }
  }
};
</script>

<style scoped="scoped">
.indexbill {
  width: 100%;
  height: 745px;
  overflow: hidden;
  background: #ffffff;
  position: relative;
  top: 0;
}
#ul_1 {
  width: 90%;
  margin: auto;
  margin-top: 40px;
  overflow: hidden;
}
.class_1 {
  width: 400px;
  height: 40px;
  text-align: center;
  line-height: 40px;
  background: #ffc600;
  color: #ffffff;
  margin: auto;
  margin-top: 100px;
  border-radius: 10px;
  cursor: pointer;
}
.class_2 {
  background: #cccccc;
  cursor:none;
}
#ul_1 > li {
  width: 16.6666666%;
  float: left;
  text-align: center;
}
#ul_1 > li > div:nth-of-type(1) {
  margin-bottom: 20px;
  font-size: 18px;
}
#ul_1 > li > div:nth-of-type(2) {
  color: #ffc600;
}
</style>