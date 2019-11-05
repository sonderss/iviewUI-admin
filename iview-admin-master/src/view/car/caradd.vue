<template>
<div class="divtop">
    <Form ref="formCustom" :model="formCustom" :rules="ruleCustom" :label-width="80" class="test" >
        <FormItem label="标题：" prop="passwd">
            <Input type="password" v-model="formCustom.passwd" style="width:70%;"></Input>
        </FormItem>
        <FormItem label="分类：" prop="passwdCheck">
             <Dropdown trigger="click" style="width:70%;background:#fff;border:1px solid #ccc; " @on-click='getValue'>
                <a href="javascript:void(0)" style="display:block;width:100%;">

                    <Icon type="ios-arrow-down" style="margin-left:98%"> 轿车</Icon>
                </a>
                <DropdownMenu slot="list" >
                    <DropdownItem >轿车</DropdownItem>
                    <DropdownItem>商用车</DropdownItem>
                    <DropdownItem>二手车</DropdownItem>
                    <DropdownItem>SUV</DropdownItem>
                    <DropdownItem>新能源货车</DropdownItem>
                </DropdownMenu>
            </Dropdown>
        </FormItem>
        <FormItem label="品牌：" prop="pinpai">
            <Dropdown trigger="click" style="width:70%;background:#fff;border:1px solid #ccc;">
                <a href="javascript:void(0)" style="display:block;width:100%;">
                    <Icon type="ios-arrow-down" style="margin-left:98%"></Icon>
                </a>
                <DropdownMenu slot="list">
                    <DropdownItem >奔驰</DropdownItem>
                    <DropdownItem>奥迪</DropdownItem>
                    <DropdownItem>五菱</DropdownItem>
                    <DropdownItem>景逸</DropdownItem>
                    <DropdownItem>奔腾</DropdownItem>
                </DropdownMenu>
            </Dropdown>
        </FormItem>
         <FormItem label="排序：" prop="sort">
            <Input type="text" v-model="formCustom.age" number style="width:70%;"></Input>
        </FormItem>
         <FormItem label="价格：" prop="price">
            <Input type="text" v-model="formCustom.age" number style="width:70%;"></Input>
        </FormItem>
          <FormItem label="缩略图">
            <Upload
                ref="upload"
                :show-upload-list="false"
                :default-file-list="defaultList"
                :on-success="handleSuccess"
                :format="['jpg','jpeg','png']"
                :max-size="2048"
                :on-format-error="handleFormatError"
                :on-exceeded-size="handleMaxSize"
                :before-upload="handleBeforeUpload"
                multiple
                type="drag"
                action="//jsonplaceholder.typicode.com/posts/"
                style="display: inline-block;width:58px;">
                <div style="width: 58px;height:58px;line-height: 58px;">
                    <Icon type="ios-camera" size="20"></Icon>
                </div>
            </Upload>
        </FormItem>
         <FormItem label="车辆信息" prop="msg">
          <quillEditor style="width:70%;height:300px"></quillEditor>
        </FormItem>
        <FormItem style="margin-top:100px">
            <Button type="primary" @click="handleSubmit('formCustom')">保存</Button>
            <Button @click="handleReset('formCustom')" style="margin-left: 8px">取消</Button>
        </FormItem>
    </Form>
</div>
</template>
<script>
import { quillEditor } from 'vue-quill-editor'
export default {
  components: { quillEditor },
  data () {
    const validatePass = (rule, value, callback) => {
      if (value === '') {
        callback(new Error('Please enter your password'))
      } else {
        if (this.formCustom.passwdCheck !== '') {
          // 对第二个密码框单独验证
          this.$refs.formCustom.validateField('passwdCheck')
        }
        callback()
      }
    }
    const validatePassCheck = (rule, value, callback) => {
      if (value === '') {
        callback(new Error('Please enter your password again'))
      } else if (value !== this.formCustom.passwd) {
        callback(new Error('The two input passwords do not match!'))
      } else {
        callback()
      }
    }
    const validateAge = (rule, value, callback) => {
      if (!value) {
        return callback(new Error('Age cannot be empty'))
      }
      // 模拟异步验证效果
      setTimeout(() => {
        if (!Number.isInteger(value)) {
          callback(new Error('Please enter a numeric value'))
        } else {
          if (value < 18) {
            callback(new Error('Must be over 18 years of age'))
          } else {
            callback()
          }
        }
      }, 1000)
    }

    return {
      formCustom: {
        passwd: '',
        passwdCheck: '',
        age: ''
      },
      ruleCustom: {
        passwd: [
          { validator: validatePass, trigger: 'blur' }
        ],
        passwdCheck: [
          { validator: validatePassCheck, trigger: 'blur' }
        ],
        age: [
          { validator: validateAge, trigger: 'blur' }
        ]
      }
    }
  },
  methods: {
    handleSubmit (name) {
      this.$refs[name].validate((valid) => {
        if (valid) {
          this.$Message.success('Success!')
        } else {
          this.$Message.error('Fail!')
        }
      })
    },
    handleReset (name) {
      this.$refs[name].resetFields()
    },
    getValue (name) {
      console.log(name)
    }
  }
}
</script>

<style scoped>
    .test{
     width: 100%;
     margin:0 auto

    }
     Input{
            width: 70%
        }
        .divtop{
            width: 100%;
             margin-left:100px;

        }

</style>
