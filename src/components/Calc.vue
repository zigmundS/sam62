<template>
  <el-container>
  <el-header>

  </el-header>
  <el-main>
    <el-form :inline="true" :model="formInline" class="demo-form-inline">
      <el-form-item label="Approved by">
        <el-input v-model="formInline.user" placeholder="Approved by"></el-input>
      </el-form-item>
      <el-form-item label="Activity zone">
        <el-select v-model="formInline.region" placeholder="Activity zone">
          <el-option label="Zone one" value="shanghai"></el-option>
          <el-option label="Zone two" value="beijing"></el-option>
        </el-select>
      </el-form-item>
      <el-form-item>
        <el-button type="primary" @click="onSubmit">Query</el-button>
      </el-form-item>
    </el-form>
    <el-form :model="numberValidateForm" ref="numberValidateForm" label-width="100px" class="demo-ruleForm">
      <el-form-item
        label="age"
        prop="age"
        :rules="[
          { required: true, message: 'age is required'},
          { type: 'number', message: 'age must be a number'}
        ]"
      >
        <el-input type="age" v-model.number="numberValidateForm.age" auto-complete="off"></el-input>
      </el-form-item>
    </el-form>


  </el-main>
  <el-footer>Footer</el-footer>
</el-container>
</template>

<script>
export default {
  name: 'Калькулятор',
  data () {
    return {
      numberValidateForm: {
          age: ''
        },
      form: {
          name: '',
          region: '',
          date1: '',
          date2: '',
          delivery: false,
          type: [],
          resource: '',
          desc: ''
        },
      formInline: {
        user: '',
        region: ''
      }
    }
  },
  methods: {
      onSubmit() {
        console.log('submit!');
      }
    }
}
</script>

<style>

</style>
