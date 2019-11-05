<template>
    <div>
          <Table border :columns="columns12" :data="data6">
        <template slot-scope="{ row }" slot="name">
            <strong>{{ row.name }}</strong>
        </template>
        <template slot-scope="{ row, index }" slot="action">
            <Button type="primary" size="small" style="margin-right: 5px" @click="show(index)">View</Button>
            <Button type="error" size="small" @click="remove(index)">Delete</Button>
        </template>

    </Table>
        <div style="width:100%;display:flex">
            <Page :total="100" style="margin:30px auto"/>
        </div>
    </div>
</template>
<script>
export default {
  data () {
    return {
      columns12: [
        {
          type: 'selection',
          width: 60,
          align: 'center'
        },
        {
          title: 'Id',

          key: 'Id',
          align: 'center'
        },
        {
          title: '分类',
          key: 'fenlei',
          align: 'center'
        },
        {
          title: '标题',
          key: 'title',
          align: 'center'
        },
        {
          title: '图片',
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
          title: '排序',
          key: 'sort',
          align: 'center'
        },
        {
          title: '添加时间',
          key: 'addtime',
          align: 'center'

        },
        {
          title: '操作',
          slot: 'step',
          width: 150,
          align: 'center',
          render: (h, params) => {
            return h('div', [
              h('Button', {
                props: {
                  type: 'primary',
                  size: 'small'
                },
                style: {
                  marginRight: '5px'
                },
                on: {
                  click: () => {
                    this.show(params.index)
                  }
                }
              }, '查看'),
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
          Id: '40',
          title: '租车服务',
          photo: 'https://zqjrqc.cmh8.cn/upload/20180807/df9610f871acaa75856d4edd37864c4e.jpg',
          href: '/pages/index/debug',
          sort: '10039',
          addtime: '2018-06-20 16:25:07',
          fenlei: '乘用车'
        },
        {
          Id: '40',
          title: '购车流程',
          photo: 'https://zqjrqc.cmh8.cn/upload/20180820/77e20ef5f2f5c7e99dcce4c9df2920d0.jpg',
          href: '/pages/index/debug',
          sort: '10039',
          addtime: '2018-06-20 16:25:07',
          fenlei: '乘用车'
        },
        {
          Id: '40',
          title: '年审代理',
          photo: 'https://zqjrqc.cmh8.cn/upload/20180820/298f16581d2262844aa015eaa315d923.jpg',
          href: '/pages/index/debug',
          sort: '10039',
          addtime: '2018-06-20 16:25:07',
          fenlei: '乘用车'
        },
        {
          Id: '40',
          title: '财务代理',
          photo: 'https://zqjrqc.cmh8.cn/upload/20180820/3f32a3c6866be83328535a81b5902349.jpg',
          href: '/pages/index/debug',
          sort: '10039',
          addtime: '2018-06-20 16:25:07',
          fenlei: '乘用车'
        }
      ]
    }
  },
  methods: {
    show (index) {
      this.$Modal.info({
        title: 'User Info',
        content: `车型：${this.data6[index].title}<br>路径：${this.data6[index].href}<br>添加时间：${this.data6[index].addtime}`
      })
    },
    remove (index) {
      this.data6.splice(index, 1)
    }
  }
}
</script>

<style lang="">

</style>
