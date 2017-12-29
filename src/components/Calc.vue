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
    <el-form :model="numberValidateForm" ref="numberValidateForm" label-width="200px" class="demo-ruleForm">
      <el-form-item
        label="объём"
        prop="obm"
        :rules="[
          { required: true, message: 'is required'},
          { type: 'number', message: 'must be a number'}
        ]"
      >
        <el-input type="obm" v-model.number="numberValidateForm.obm" auto-complete="off"></el-input>
      </el-form-item>
      <el-form-item
        label="градус"
        prop="grad"
        :rules="[
          { required: true, message: 'is required'},
          { type: 'number', message: 'must be a number'}
        ]"
      >
        <el-input type="grad" v-model.number="numberValidateForm.grad" auto-complete="off"></el-input>
      </el-form-item>
      <el-form-item
        label="новый градус"
        prop="newgrad"
        :rules="[
          { required: true, message: 'is required'},
          { type: 'number', message: 'must be a number'}
        ]"
      >
        <el-input type="newgrad" v-model.number="numberValidateForm.newgrad" auto-complete="off"></el-input>
      </el-form-item>
      <el-form-item
        label="новый объём"
        prop="newobm"
        :rules="[
          { type: 'number', message: 'must be a number'}
        ]"
      >
        <el-input type="newobm" v-model.number="newobm" auto-complete="off"></el-input>
      </el-form-item>
    </el-form>
    <el-button type="button" @click="calc">calc</el-button>

    <h2>{{ numberValidateForm.voda }}</h2>


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
          obm: '',
          grad: '',
          newobm: '',
          newgrad: '',
          voda: ''
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
      },
      calc() {
        this.numberValidateForm.voda = this.numberValidateForm.obm * (this.numberValidateForm.grad / this.numberValidateForm.newgrad - 1);
        // this.numberValidateForm.newobm = this.numberValidateForm.voda + this.numberValidateForm.obm;
      }
    },
    computed: {
      newobm() {
            return this.numberValidateForm.voda + this.numberValidateForm.obm;
        },
    }
}
</script>

<style>

</style>
