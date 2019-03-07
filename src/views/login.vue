<template>
  <Form
    ref="formValidate"
    :model="formValidate"
    :rules="ruleValidate"
    :label-width="80"
  >
    <img src="../assets/amaze.jpg" alt class="login-img" />
    <FormItem prop="name">
      <Icon type="ios-contact" size="30"></Icon>
      <Input
        v-model="formValidate.name"
        placeholder="姓名"
        @focus="handleSubmit('formValidate')"
      />
    </FormItem>
    <FormItem prop="password">
      <Icon type="ios-key" size="30"></Icon>
      <Input
        v-model="formValidate.password"
        placeholder="密码"
        @focus="handleSubmit('formValidate')"
      />
    </FormItem>
    <FormItem>
      <Button type="primary" @click="handleSubmit('formValidate')">登录</Button>
    </FormItem>
  </Form>
</template>

<script>
export default {
  data() {
    return {
      formValidate: {
        name: "",
        password: ""
      },
      ruleValidate: {
        name: [
          {
            required: true,
            message: "姓名不能为空",
            trigger: "blur"
          }
        ],
        password: [
          {
            required: true,
            message: "密码不能为空",
            trigger: "blur"
          }
        ]
      }
    };
  },
  methods: {
    handleSubmit(name) {
      this.$refs[name].validate(valid => {
        if (valid) {
          this.$Message.success("Success!");
        } else {
          this.$Message.error("Fail!");
        }
      });
    },
    handleReset(name) {
      this.$refs[name].resetFields();
    }
  }
};
</script>
