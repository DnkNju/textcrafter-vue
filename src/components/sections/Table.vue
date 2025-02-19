<script lang="ts" setup>

// 表格数据
const tableData = [
{
    model: 'SD3.5 Large (ICML 2024)',
    word_accuracy: '0.6548',
    ned: '0.8470',
    clip_score: '0.7797',
},
{
    model: 'FLUX.1 dev (2024)',
    word_accuracy: '0.4965',
    ned: '0.6879',
    clip_score: '0.7401',
},
{
    model: 'AnyText (ICLR 2024)',
    word_accuracy: '0.1804',
    ned: '0.4675',
    clip_score: '0.7432',
},
{
    model: 'TextDiffuser-2 (ECCV 2024)',
    word_accuracy: '0.2326',
    ned: '0.4353',
    clip_score: '0.6765',
},
{
    model: 'RAG-Diffusion (Arxiv 2024)',
    word_accuracy: '0.2648',
    ned: '0.4498',
    clip_score: '0.7797',
},
{
    model: '3DIS (ICLR 2025)',
    word_accuracy: '0.3813',
    ned: '0.6505',
    clip_score: '0.7767',
},
{
    model: 'TextCrafter (Ours)',
    word_accuracy: '0.7370',
    ned: '0.8679',
    clip_score: '0.7868',
},
]
</script>

<template>
    <div>
        <el-divider />

        <el-row justify="center">
            <h1 class="section-title">Qualitative Results</h1>
        </el-row>
        
        <!-- 数据表格 -->
        <el-row justify="center">
            <el-col :xs="24" :sm="20" :md="16" :lg="12" :xl="12">

                <!-- 卡片 -->
                <el-card class="card">

                    <!-- 默认tab -->
                    <el-tabs class="demo-tabs" model-value="CVTG-2K">

                    <!-- 第一个tab -->
                    <el-tab-pane label="CVTG-2K" name="CVTG-2K">

                        <!-- 表格数据 -->
                        <el-table 
                            :data="tableData"
                            :default-sort="{ prop: 'value_b', order: 'descending' }"
                            scrollbar-always-on
                        >
                            <el-table-column prop="model" label="Model" width="250" sortable/>
                            <el-table-column prop="word_accuracy" label="Word Accuracy" min-width="150" sortable/>
                            <el-table-column prop="ned" label="NED" min-width="120" sortable/>
                            <el-table-column prop="clip_score" label="CLIPScore" min-width="120" sortable/>
                        </el-table>
                    </el-tab-pane>

                    <!-- <el-tab-pane label="Method B" name="Method B">
                        Method B
                    </el-tab-pane>

                    <el-tab-pane label="Method C" name="Method C">
                        Method C
                    </el-tab-pane>

                    <el-tab-pane label="Method D" name="Method D">
                        Method D
                    </el-tab-pane> -->
                    </el-tabs>

                </el-card>
            </el-col>
        </el-row>

    </div>
</template>

<style scoped>
.card {
    margin-top: 20px;
}
</style>
  