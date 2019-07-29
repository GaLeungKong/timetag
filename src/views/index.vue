<template>
    <div>
        <el-header>this is header</el-header>
        <el-container>
            <el-aside width="20%"></el-aside>
            <el-container>
                <el-row>
                  <el-col :span="12">col_1</el-col>
                  <el-col :span="12">col_2</el-col>
                </el-row>
            </el-container>
        </el-container>
        <el-footer></el-footer>
    </div>
</template>