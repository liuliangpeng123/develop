<template>
  <a-modal
    title="日志详情"
    :width="900"
    :visible="visible"
    :confirmLoading="confirmLoading"
    @cancel="handleCancel"
  >
    <a-spin :spinning="confirmLoading">
      <a-form :form="form">
        <a-row :gutter="24">
          <a-col :md="12" :sm="24">
            <a-form-item
              label="请求地址"
              :labelCol="labelCol"
              :wrapperCol="wrapperCol"
            >
              <a-input v-decorator="['url']" />
            </a-form-item>
          </a-col>
          <a-col :md="12" :sm="24">
            <a-form-item
              label="请求方式"
              :labelCol="labelCol"
              :wrapperCol="wrapperCol"
            >
              <a-input v-decorator="['requestMethod']" />
            </a-form-item>
          </a-col>
        </a-row>
        <a-row :gutter="24">
          <a-col :md="12" :sm="24">
            <a-form-item
              label="请求路径"
              :labelCol="labelCol"
              :wrapperCol="wrapperCol"
            >
              <a-input v-decorator="['path']" />
            </a-form-item>
          </a-col>
          <a-col :md="12" :sm="24">
            <a-form-item
              label="操作人"
              :labelCol="labelCol"
              :wrapperCol="wrapperCol"
            >
              <a-input v-decorator="['account']" />
            </a-form-item>
          </a-col>
        </a-row>
        <a-row :gutter="24">
          <a-col :md="12" :sm="24">
            <a-form-item
              label="浏览器"
              :labelCol="labelCol"
              :wrapperCol="wrapperCol"
            >
              <a-input v-decorator="['browser']" />
            </a-form-item>
          </a-col>
          <a-col :md="12" :sm="24">
            <a-form-item
              label="操作系统"
              :labelCol="labelCol"
              :wrapperCol="wrapperCol"
            >
              <a-input v-decorator="['operatingSystem']" />
            </a-form-item>
          </a-col>
        </a-row>
        <a-row :gutter="24">
          <a-col :md="12" :sm="24">
            <a-form-item
              label="执行结果"
              :labelCol="labelCol"
              :wrapperCol="wrapperCol"
            >
              <a-input :rows="4" v-decorator="['success']" />
            </a-form-item>
          </a-col>
          <a-col :md="12" :sm="24">
            <a-form-item
              label="具体消息"
              :labelCol="labelCol"
              :wrapperCol="wrapperCol"
            >
              <a-input :rows="4" v-decorator="['message']"/>
            </a-form-item>
          </a-col>
        </a-row>
        <a-row :gutter="24">
          <a-col :md="12" :sm="24">
            <a-form-item
              label="请求body"
              :labelCol="labelCol"
              :wrapperCol="wrapperCol"
            >
              <a-textarea :rows="4" v-decorator="['body']"/>
            </a-form-item>
          </a-col>
          <a-col :md="12" :sm="24">
            <a-form-item
              label="返回结果"
              :labelCol="labelCol"
              :wrapperCol="wrapperCol"
            >
              <a-textarea :rows="4" v-decorator="['result']"/>
            </a-form-item>
          </a-col>
        </a-row>
      </a-form>
    </a-spin>
  </a-modal>
</template>
<script>
  export default {
    data () {
      return {
        labelCol: {
          xs: { span: 24 },
          sm: { span: 4 }
        },
        wrapperCol: {
          xs: { span: 24 },
          sm: { span: 18 }
        },
        visible: false,
        confirmLoading: false,
        form: this.$form.createForm(this)
      }
    },
    methods: {
      // 初始化方法
      details (record) {
        this.visible = true
        setTimeout(() => {
          this.form.setFieldsValue(
            {
              url: record.url,
              path: record.path,
              requestMethod: record.requestMethod,
              account: record.account,
              browser: record.browser,
              operatingSystem: record.operatingSystem,
              success: record.success,
              body: record.body,
              result: record.result,
              message: record.message
            }
          )
        }, 100)
      },
      handleCancel () {
        this.form.resetFields()
        this.visible = false
      }
    }
  }
</script>
