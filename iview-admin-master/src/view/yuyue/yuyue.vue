<template>
    <div>
    <Layout>
        <Header style="color:#fff;display:flex; justify-content: space-between;align-items: center">
            <p>买车预约管理</p>
             <Button style="height:40px" type="primary" size='default'>导出</Button>
        </Header>

    </Layout>
      <Table border :columns="columns7" :data="data6"></Table>
    </div>
</template>
<script>
export default {
  data () {
    return {
      columns7: [
        // {
        //   title: 'Name',
        //   key: 'name',
        //   render: (h, params) => {
        //     return h('div', [
        //       h('Icon', {
        //         props: {
        //           type: 'person'
        //         }
        //       }),
        //       h('strong', params.row.name)
        //     ])
        //   }
        // },
        {
          title: 'ID',
          key: 'id',
          align: 'center'
        },
        {
          title: '车辆封面图',
          key: 'photo',
          align: 'center',
          render: (h, params) => {
            return h('div', [
              h('img', {
                domProps: {
                  src: params.row.photo
                },
                style: {
                  width: '150px',
                  height: '150px',
                  display: 'block',
                  margin: '0 auto',
                  boxShadow: '0px 0px 1px 0 #dedede'
                }
              }, 'View')
            ])
          }
        },
        {
          title: '姓名',
          key: 'name',
          align: 'center'
        },
        {
          title: '手机号码',
          key: 'phone',
          align: 'center'
        },
        {
          title: '提交时间',
          key: 'time',
          align: 'center'
        },
        {
          title: '状态',
          key: 'status',
          align: 'center',
          render: (h, params) => {
            return h('div', [
              h('Button', {
                domProps: {
                  src: params.row.status
                },
                style: {
                  width: '70px',
                  height: '30px',
                  display: 'block',
                  margin: '0 auto',
                  background: '#ff5555',
                  color: '#fff'
                }
              }, '未回复')
            ])
          }
        },
        {
          title: '操作',
          key: 'action',
          width: 150,
          align: 'center',
          render: (h, params) => {
            return h('div', [

              h('Button', {
                props: {
                  type: 'error',
                  size: 'small'
                },
                on: {
                  click: () => {
                    this.remove(params.index)
                  }
                }
              }, '删除')
            ])
          }
        }
      ],
      data6: [
        {
          id: 51,
          name: '陈生',
          photo: 'https://zqjrqc.cmh8.cn/upload/20191023/b7bb608d495ef153b36a4bbccb96c870.jpg',
          phone: '18316875855',
          time: '2019-10-23 17:57:50',
          status: '未回复'
        },
        {
          id: 51,
          name: '陈生',
          photo: 'https://zqjrqc.cmh8.cn/upload/20191023/b7bb608d495ef153b36a4bbccb96c870.jpg',
          phone: '18316875855',
          time: '2019-10-23 17:57:50',
          status: '未回复'
        },
        {
          id: 51,
          name: '陈生',
          photo: 'https://zqjrqc.cmh8.cn/upload/20191023/b7bb608d495ef153b36a4bbccb96c870.jpg',
          phone: '18316875855',
          time: '2019-10-23 17:57:50',
          status: '未回复'
        },
        {
          id: 51,
          name: '陈生',
          photo: 'https://zqjrqc.cmh8.cn/upload/20191023/b7bb608d495ef153b36a4bbccb96c870.jpg',
          phone: '18316875855',
          time: '2019-10-23 17:57:50',
          status: '未回复'
        }
      ]
    }
  },
  methods: {
    show (index) {
      this.$Modal.info({
        title: 'User Info',
        content: `Name：${this.data6[index].name}<br>Age：${this.data6[index].age}<br>Address：${this.data6[index].address}`
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
