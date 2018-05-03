<template>
    <section>
        <!--工具条-->
        <el-col :span="24" class="toolbar" style="padding-bottom: 0px;">
            <el-form :inline="true" style="float: right">
                <el-form-item>
                    <el-button icon="el-icon-circle-plus" type="primary" @click="">新增一级栏目</el-button>
                </el-form-item>
            </el-form>
        </el-col>

        <el-table
                :data="tableData"
                style="width: 100%">
            <el-table-column
                    label="日期"
                    width="250">
                <template slot-scope="scope">
                    <i class="el-icon-time"></i>
                    <span style="margin-left: 10px">{{ scope.row.date }}</span>
                </template>
            </el-table-column>
            <el-table-column
                    label="姓名"
                    width="200">
                <template slot-scope="scope">
                    <div slot="reference" class="name-wrapper">
                        <el-tag size="medium">{{ scope.row.name }}</el-tag>
                    </div>
                </template>
            </el-table-column>
            <el-table-column label="操作">
                <template slot-scope="scope">
                    <el-button
                            size="mini"
                            @click="handleEdit_one(scope.$index, scope.row)">编辑二级栏目
                    </el-button>
                    <el-button
                            size="mini"
                            type="danger"
                            @click="handleDelete_one(scope.$index, scope.row)">删除
                    </el-button>
                </template>
            </el-table-column>
        </el-table>

        <!-- Table -->
        <el-dialog title="收货地址" :visible.sync="dialogTableVisible">
            <!--工具条-->
            <el-button icon="el-icon-circle-plus" type="primary" @click="" style="float: right;">新增二级栏目</el-button>
            <el-table :data="gridData">
                <el-table-column property="date" label="日期" width="200"></el-table-column>
                <el-table-column property="name" label="姓名" width="200"></el-table-column>
                <el-table-column label="操作">
                    <template slot-scope="scope">
                        <el-button
                                size="mini"
                                @click="handleEdit_two(scope.$index, scope.row)">编辑
                        </el-button>
                        <el-button
                                size="mini"
                                type="danger"
                                @click="handleDelete_two(scope.$index, scope.row)">删除
                        </el-button>
                    </template>
                </el-table-column>
            </el-table>
        </el-dialog>

        <!-- Form -->
        <el-dialog title="收货地址" :visible.sync="dialogFormVisible">
            <el-form :model="form">
                <el-form-item label="活动名称" label-width="120px">
                    <el-input v-model="form.id" auto-complete="off" placeholder="请输入xxxx"></el-input>
                </el-form-item>
                <el-form-item label="活动名称" label-width="120px">
                    <el-input v-model="form.name" auto-complete="off" placeholder="请输入xxxx"></el-input>
                </el-form-item>
            </el-form>
            <div slot="footer" class="dialog-footer">
                <el-button @click="dialogFormVisible = false">取 消</el-button>
                <el-button type="primary" @click="dialogFormVisible = false">确 定</el-button>
            </div>
        </el-dialog>

    </section>
</template>

<script>
    export default {
        data() {
            return {
                tableData: [{
                    date: '2016-05-02',
                    name: '上海新闻',
                }, {
                    date: '2016-05-04',
                    name: '艺术人生',
                }, {
                    date: '2016-05-01',
                    name: '学期教育',
                }, {
                    date: '2016-05-03',
                    name: '人文艺术',
                }],
                gridData: [{
                    date: '123123123123',
                    name: '二级栏目1',
                }, {
                    date: '123123123123',
                    name: '二级栏目2',
                }, {
                    date: '412312312331',
                    name: '二级栏目3',
                }],
                dialogTableVisible: false,
                dialogFormVisible: false,
                form:{
                    name:'',
                    id:''
                }

            }
        },
        methods: {
            handleEdit_one(index, row) {
                console.log(index, row);
                this.dialogTableVisible = true;
            },
            handleDelete_one(index, row) {
                console.log(index, row);
            },
            handleEdit_two(index, row) {
                console.log(index, row);
                this.dialogFormVisible = true;
            },
            handleDelete_two(index, row) {
                console.log(index, row);
            }
        }
    }
</script>