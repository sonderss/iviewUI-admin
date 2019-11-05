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
    </div>
</template>
<script>
export default {
  data () {
    return {
      columns12: [
        {
          title: 'Id',

          key: 'Id',
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
          title: '链接',
          key: 'href',
          align: 'center'
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
          title: 'banner2',
          photo: 'https://zqjrqc.cmh8.cn/upload/20180807/df9610f871acaa75856d4edd37864c4e.jpg',
          href: '/pages/index/debug',
          sort: '10039',
          addtime: '2018-06-20 16:25:07'
        },
        {
          Id: '40',
          title: 'title_debug39',
          photo: 'https://zqjrqc.cmh8.cn/upload/20180807/c52a4d816db0196bc7e995ee57fb71f1.jpg',
          href: '/pages/index/debug',
          sort: '10039',
          addtime: '2018-06-20 16:25:07'
        },
        {
          Id: '40',
          title: 'title_debug37',
          photo: 'https://zqjrqc.cmh8.cn/upload/20180806/c95d98c12d2c38062912f5e897d59d32.jpg',
          href: '/pages/index/debug',
          sort: '10039',
          addtime: '2018-06-20 16:25:07'
        }
      ]
    }
  },
  methods: {
    show (index) {
      this.$Modal.info({
        title: 'User Info',
        content: `Name：${this.data6[index].title}<br>Age：${this.data6[index].href}<br>Address：${this.data6[index].addtime}`
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
