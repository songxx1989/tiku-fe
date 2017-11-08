<template>
  <div>
    <el-form ref="form" :model="form" label-width="80px">

      <el-form-item label="题目分类">
        <el-select v-model="form.cid" placeholder="请选择题目分类">
          <el-option label="分类1" value="shanghai"></el-option>
          <el-option label="分类2" value="beijing"></el-option>
        </el-select>
      </el-form-item>
      <el-form-item label="题目难度">
        <el-select v-model="form.lid" placeholder="请选择题目难度">
          <el-option label="难度1" value="shanghai"></el-option>
          <el-option label="难度2" value="beijing"></el-option>
        </el-select>
      </el-form-item>
      <el-form-item label="题干">
        <el-input type="textarea" v-model="form.text"></el-input>
      </el-form-item>
      <el-form-item>
        <el-button type="primary" @click="onSubmit">立即创建</el-button>
        <el-button>取消</el-button>
      </el-form-item>
    </el-form>

    <el-table
      :data="tableData">
      <el-table-column
        prop="id"
        label="编号">
      </el-table-column>
      <el-table-column
        prop="cid"
        label="分类">
      </el-table-column>
      <el-table-column
        prop="lid"
        label="难度">
      </el-table-column>
      <el-table-column
        prop="text"
        label="题目">
      </el-table-column>
    </el-table>
  </div>
</template>

<script>
  import axios from 'axios'

  export default {
    name: 'HelloWorld',
    created () {
      let self = this
      axios.get('http://localhost:8080/ques')
        .then(resp => self.tableData = resp.data)
        .catch(err => console.log(err))
    },
    data () {
      return {
        tableData: [],
        form: {cid: '', lid: '', text: ''}
      }
    },
    methods: {
      onSubmit () {
        console.log('submit!')
      }
    }
  }
</script>
