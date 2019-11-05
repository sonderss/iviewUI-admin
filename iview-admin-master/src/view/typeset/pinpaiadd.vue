<template>
<div>
    <Layout>
        <Header style="color:#fff;display:flex; justify-content: space-between;align-items: center">
            <p>品牌添加</p>
        </Header>
    </Layout>
    <div class="test">
            <p class="txt">分类名称：</p>
              <Input v-model="value" placeholder="Enter something..." style="width: 70%;height:40px" />
    </div>
     <div class="test">
            <p class="txt">排序：</p>
              <Input v-model="value" placeholder="Enter something..." style="width: 70%;height:40px" />

    </div>
    <div class="test">
         <Button  :size="buttonSize" icon="md-document" type="primary">保存</Button>
       <Button style="margin-left:15px">取消</Button>
    </div>

</div>
</template>

<script>
export default {
  data () {
    return {
      value: ''
    }
  }
}
</script>
<style scoped>
.test{
display: flex;
justify-content: flex-start;
align-items: center;
margin-left: 50px;
margin-top:50px
}
.txt{
    width: 60px
}
</style>
