<template>
  <div>

    <div>
      <div style="display: flex">
        <div class="form1-css">
          <Form ref="formValidate" :model="formValidate" :rules="ruleValidate" :label-width="80">
            <FormItem label="视图" prop="city">
              <Select v-model="formValidate.city" placeholder="">
                <Option value="beijing">本周会议</Option>
                <Option value="shanghai">London</Option>
                <Option value="shenzhen">Sydney</Option>
              </Select>
            </FormItem>
            <FormItem label="关联议题" prop="name">
              <Input v-model="formValidate.name" placeholder=""></Input>
            </FormItem>
            <FormItem label="参会人员" prop="mail">
              <Input v-model="formValidate.mail" placeholder=""></Input>
            </FormItem>

          </Form>
        </div>
        <div class="form1-css form2-css">
          <Form ref="formValidate" :model="formValidate" :rules="ruleValidate" :label-width="80">
            <FormItem label="会议主题" prop="name">
              <Input v-model="formValidate.name" placeholder=""></Input>
            </FormItem>
            <FormItem label="会议时间" prop="mail">
              <Input v-model="formValidate.mail" placeholder=""></Input>
            </FormItem>
            <FormItem label="会议未开始">
              <i-switch v-model="formValidate.switch" size="large">
                <span slot="open">On</span>
                <span slot="close">Off</span>
              </i-switch>
            </FormItem>
          </Form>
        </div>
        <div class="form1-css form3-css">
          <Form ref="formValidate" :model="formValidate" :rules="ruleValidate" :label-width="80">
            <FormItem label="类型" prop="city">
              <Select v-model="formValidate.city" placeholder="">
                <Option value="beijing">讨论会</Option>
                <Option value="shanghai">London</Option>
                <Option value="shenzhen">Sydney</Option>
              </Select>
            </FormItem>
            <FormItem label="参会部门" prop="mail">
              <Input v-model="formValidate.mail" placeholder=""></Input>
            </FormItem>
            <FormItem label="  " prop="">

            </FormItem>
          </Form>
        </div>
      </div>
      <div style="border: 2px solid #eee;
    text-align: center;
    padding: 10px;    width: 99%;
    border-top: 0;">
        <Button type="warning">重置</Button>
        <Button type="success" style="margin-left: 50px">查询</Button>
      </div>
    </div>

  <div style="width: 99%">
    <div style="    margin: 20px 0;" class="tabBtn">
      <Button>新增</Button>
      <Button>删除</Button>
    </div>
      <Table border ref="selection" :columns="columns5" :data="data5"></Table>

  </div>
  <div style="margin-top: 20px">
    <Page :total="40" size="small" show-elevator show-sizer show-total/>
  </div>
  </div>

</template>
<script>
export default {
  data () {
    return {
      columns5: [
        {
          title: 'Date',
          key: 'date',
          sortable: true,
          type: 'selection',
          width: 50
        },
        {
          title: '序号',
          type: 'index',
          width: 50,
          align: 'center'
        },
        {
          title: '操作',
          key: 'action',
          fixed: 'right',
          width: 120,
          render: (h, params) => {
            return h('div', [
              h('Button', {
                props: {
                  type: 'text',
                  size: 'small'
                }
              }, '编辑'),
              h('Button', {
                props: {
                  type: 'text',
                  size: 'small'
                }
              }, '删除')
            ])
          }
        },
        {
          title: '会议主题',
          key: 'hyzt',
          sortable: true
        },
        {
          title: '类型',
          key: 'lx',
          sortable: true
        },
        {
          title: '关联议题',
          key: 'glyt'
        },
        {
          title: '会议时间',
          key: 'hysj'
        },
        {
          title: '参会部门',
          key: 'chbm'
        },
        {
          title: '参会人员',
          key: 'chry'
        },
        {
          title: '创建人',
          key: 'cjr',
          sortable: true
        },
        {
          title: '创建时间',
          key: 'cjsj',
          sortable: true
        },
        {
          title: '修改人',
          key: 'xgr',
          sortable: true
        },
        {
          title: '修改时间',
          key: 'xgsj',
          sortable: true
        }
      ],
      data5: [
        {
          hyzt: '关于xx项目的汇报会',
          lx: '讨论会',
          glyt: 'xx议题',
          hysj: '今天14：30',
          chbm: '基建部',
          chry: '王某某',
          cjr: '李文',
          cjsj: '2020:-06-04 12:33:08',
          xgr: '李文',
          xgsj: '2020:-06-04 12:33:08'
        },
        {
          hyzt: '关于xx项目的汇报会',
          lx: '讨论会',
          glyt: 'xx议题',
          hysj: '今天14：30',
          chbm: '基建部',
          chry: '王某某',
          cjr: '李文',
          cjsj: '2020:-06-04 12:33:08',
          xgr: '李文',
          xgsj: '2020:-06-04 12:33:08'
        },
        {
          hyzt: '关于xx项目的汇报会',
          lx: '讨论会',
          glyt: 'xx议题',
          hysj: '今天14：30',
          chbm: '基建部',
          chry: '王某某',
          cjr: '李文',
          cjsj: '2020:-06-04 12:33:08',
          xgr: '李文',
          xgsj: '2020:-06-04 12:33:08'
        }

      ],
      formValidate: {
        name: '',
        mail: '',
        switch: true,
        city: '',
        gender: '',
        interest: [],
        date: '',
        time: '',
        desc: ''
      },
      ruleValidate: {
        name: [
          { required: false, message: 'The name cannot be empty', trigger: 'blur' }
        ],
        mail: [
          { required: false, message: 'Mailbox cannot be empty', trigger: 'blur' },
          { type: 'email', message: 'Incorrect email format', trigger: 'blur' }
        ],
        city: [
          { required: false, message: 'Please select the city', trigger: 'change' }
        ],
        gender: [
          { required: false, message: 'Please select gender', trigger: 'change' }
        ],
        interest: [
          { required: false, type: 'array', min: 1, message: 'Choose at least one hobby', trigger: 'change' },
          { type: 'array', max: 2, message: 'Choose two hobbies at best', trigger: 'change' }
        ],
        date: [
          { required: false, type: 'date', message: 'Please select the date', trigger: 'change' }
        ],
        time: [
          { required: false, type: 'string', message: 'Please select time', trigger: 'change' }
        ],
        desc: [
          { required: false, message: 'Please enter a personal introduction', trigger: 'blur' },
          { type: 'string', min: 20, message: 'Introduce no less than 20 words', trigger: 'blur' }
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
    handleSelectAll (status) {
      this.$refs.selection.selectAll(status)
    }
  }
}
</script>
<style lang="less">
  .ivu-layout{
    background-color: transparent;
  }
  .form1-css{
    width: 33%;
    border: 1px solid #eee;
    /*padding: 10px;*/
  }
  .form2-css{
    border-left: none;
  }
  .form3-css{
    border-left: none;
  }
  .ivu-form-item{
    margin-bottom: 0;
  }
  .ivu-form-item-label{
    width: 80px;
    height: 50px;
    line-height: 28px!important;
    border: 1px solid #eee;
  }
  .ivu-form-item-content{
    margin-left: 80px;
    height: 50px;
    padding-top: 8px;
    padding-left: 10px;
    padding-right: 10px;
    border: 1px solid #eee;
  }
  .tabBtn {
    margin-left: -10px!important;
    button{
      margin-left: 10px;
    }

  }
</style>

<style>
  .ivu-table-cell {
    white-space: nowrap!important;
  }
</style>
