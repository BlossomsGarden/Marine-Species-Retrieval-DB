<template>
  <a-form @submit="handleSubmit" :form="form" class="form">

    <a-row class="form-row" :gutter="16">
      <a-col :lg="6" :md="12" :sm="24">
        <a-form-item label="界">
          <a-input 
            placeholder="请输入物种归属界" 
            v-decorator="[ 
            'kingdomName', 
            {
              initialValue:initialData.kingdomName,
              rules: [{ required: true, message: '请输入物种归属界', whitespace: true},]
            },
          ]" />
        </a-form-item>
      </a-col>
      <a-col :xl="{span: 7, offset: 1}" :lg="{span: 8}" :md="{span: 12}" :sm="24">
        <a-form-item label="门">
          <a-input 
            placeholder="请输入物种归属门" 
            v-decorator="[ 
            'phylumName', 
            {
              initialValue:initialData.phylumName,
              rules: [{ required: true, message: '请输入物种归属门', whitespace: true},]
            },
          ]" />
        </a-form-item>
      </a-col>
      <a-col :xl="{span: 9, offset: 1}" :lg="{span: 10}" :md="{span: 24}" :sm="24">
        <a-form-item label="纲">
          <a-input 
            placeholder="请输入物种归属纲" 
            v-decorator="[ 
            'className', 
            {
              initialValue:initialData.className,
              rules: [{ required: true, message: '请输入物种归属纲', whitespace: true},]
            },
          ]" />
        </a-form-item>
      </a-col>
    </a-row>

    <a-row class="form-row" :gutter="16">
      <a-col :lg="6" :md="12" :sm="24">
        <a-form-item label="目">
          <a-input 
            placeholder="请输入物种归属目" 
            v-decorator="[ 
            'orderName', 
            {
              initialValue:initialData.orderName,
              rules: [{ required: true, message: '请输入物种归属目', whitespace: true},]
            },
          ]" />
        </a-form-item>
      </a-col>
      <a-col :xl="{span: 7, offset: 1}" :lg="{span: 8}" :md="{span: 12}" :sm="24">
        <a-form-item label="科">
          <a-input 
            placeholder="请输入物种归属科" 
            v-decorator="[ 
            'familyName', 
            {
              initialValue:initialData.familyName,
              rules: [{ required: true, message: '请输入物种归属科', whitespace: true},]
            },
          ]" />  
        </a-form-item>
      </a-col>
      <a-col :xl="{span: 9, offset: 1}" :lg="{span: 10}" :md="{span: 24}" :sm="24">
        <a-form-item label="属">
          <a-input 
            placeholder="请输入物种归属" 
            v-decorator="[ 
            'genusName', 
            {
              initialValue:initialData.genusName,
              rules: [{ required: true, message: '请输入物种归属', whitespace: true},]
            },
          ]" />   
        </a-form-item>
      </a-col>
    </a-row>
    
    <a-form-item v-if="showSubmit">
      <a-button htmlType="submit" >Submit</a-button>
    </a-form-item>
  </a-form>
</template>

<script>
export default {
  name: 'TaskForm',
  props: {
    showSubmit: {
      type: Boolean,
      default: false
    },
    // 接收父组件传递的初值
    initialData: {
      type: Object,
      required: true,
    },
  },
  data () {
    return {
      form: this.$form.createForm(this)
    }
  },
  methods: {
    handleSubmit (e) {
      e.preventDefault()
      this.form.validateFields((err, values) => {
        if (!err) {
          this.$notification['error']({
            message: 'Received values of form:',
            description: values
          })
        }
      })
    }
  }
}
</script>

<style scoped>

</style>
