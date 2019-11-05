<template>
    <div>
    <Layout>
        <Header style="color:#fff;display:flex; justify-content: space-between;align-items: center">
            <p>品牌管理</p>

        </Header>

    </Layout>
      <Table border :columns="columns7" :data="data6"></Table>
      <div style="width:100%;display:flex">
            <Page :total="100" style="margin:30px auto"/>
        </div>
    </div>
</template>
<script>
export default {
  data () {
    return {
      columns7: [
        {
          type: 'selection',
          width: 60,
          align: 'center'
        },
        {
          title: 'ID',
          key: 'id',
          align: 'center'
        },
        {
          title: '品牌名称',
          key: 'name',
          align: 'center'
        },
        {
          title: '排序',
          key: 'phone',
          align: 'center'
        },
        {
          title: '提交时间',
          key: 'time',
          align: 'center'
        },
        {
          title: '操作',
          key: 'action',
          width: 150,
          align: 'center',
          render: (h, params) => {
            return h('div', [
              h('Icon', {
                props: {
                  type: 'ios-brush',
                  size: 20,
                  color: '#000'
                },
                on: {
                  click: () => {
                    this.show(params.index)
                  }
                }
              }, ''),
              h('Icon', {
                props: {
                  type: 'md-trash',
                  size: 20,
                  color: '#000'
                },
                on: {
                  click: () => {
                    this.remove(params.index)
                  }
                }
              }, '')
            ])
          }
        }
      ],
      data6: [
        {
          id: 51,
          name: '东风天龙',
          photo: 'https://zqjrqc.cmh8.cn/upload/20191023/b7bb608d495ef153b36a4bbccb96c870.jpg',
          phone: '50',
          time: '2019-10-23 17:57:50',
          status: '未回复',
          address: '青海果洛藏族自治州',
          typecar: '海马m3',
          yeartype: 2016,
          licheng: '8万公里',
          guanzhu: ''
        },
        {
          id: 51,
          name: '新能源轿车',
          photo: 'https://zqjrqc.cmh8.cn/upload/20191023/b7bb608d495ef153b36a4bbccb96c870.jpg',
          phone: '28',
          time: '2019-10-23 17:57:50',
          status: '未回复',
          address: '广州',
          typecar: '海马m3',
          yeartype: 2016,
          licheng: '8万公里',
          guanzhu: '好'
        },
        {
          id: 51,
          name: '新车特价区',
          photo: 'https://zqjrqc.cmh8.cn/upload/20191023/b7bb608d495ef153b36a4bbccb96c870.jpg',
          phone: '12',
          time: '2019-10-23 17:57:50',
          status: '未回复',
          address: '广州',
          typecar: '海马m3',
          yeartype: 2016,
          licheng: '8万公里',
          guanzhu: '好'
        },
        {
          id: 51,
          name: '东风天龙',
          photo: 'https://zqjrqc.cmh8.cn/upload/20191023/b7bb608d495ef153b36a4bbccb96c870.jpg',
          phone: '86',
          time: '2019-10-23 17:57:50',
          status: '未回复',
          address: '广州',
          typecar: '海马m3',
          yeartype: 2016,
          licheng: '8万公里',
          guanzhu: ''
        }
      ]
    }
  },
  methods: {
    show (index) {
      this.$Modal.info({
        title: '用户信息',
        content: `姓名：${this.data6[index].name}<br>手机号码：${this.data6[index].phone}<br>地址：${this.data6[index].address}`
      })
    },
    remove (index) {
      this.data6.splice(index, 1)
    }
  }
}
</script>

<style scoped>
.test{

}
</style>
