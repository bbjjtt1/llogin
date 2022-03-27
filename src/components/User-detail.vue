<template>
    <div>
    <el-container>
      <el-header class="header"> header----- {{this.$route.params.goodsId}}</el-header>

      <el-main>
          <div>
              <p>详情：{{detail.goodsPrice}}</p>
          </div>
      </el-main>

      <el-footer> </el-footer>
    </el-container>
 
 
  </div>
</template>

<script>
export default {
    data(){
        return{
            detail:{}
        }
    },

    components:{
      scroll
    },
    methods:{
        //拿管理员的数据
      getList(){
        this.$axios.get('api/usermanager/goodsall',{
            headers: this.$route.params.goodsId,
        }).then(resp => {
              if(resp.status == 200){
                this.detail = resp.data.data;
                console.log(resp);
              }else{
                this.$message.console.error("获取订单列表失败");
              }
            })
      },
    },
    created(){
        this.getList()
    }
}
</script>

<style>
    .header{
        background-color: #fff;
    }
</style>