<script>
export default {
  data() {
    return {
      value1: '',
      comparison1ImageRootPath: '',
      comparisonImageRootPath: './image_comparison/',
      comparison1Loading: true,
      options: [
        'mixed',
        'with_attributes',
        'without_attributes',
      ],
    }
  },
  beforeMount() {
    // 在组件挂载之前预加载第一张图片
    this.handleChange1(this.options[0]);
  },
  methods: {
    handleChange1(value) {
      this.loadImage1(value);
    },
    loadImage1(value) {
      this.comparison1Loading = true;
      const imagePath = `${this.comparisonImageRootPath}${value}.png`;
      // 创建一个新的Image对象用于预加载
      const image = new Image();
      image.src = imagePath;
      // 监听图片加载完成事件
      image.onload = () => {
          this.comparison1ImageRootPath = imagePath;
          this.comparison1Loading = false;
      };
    },
  },
}
</script>

<template>
  <div>
    <el-divider />

    <el-row justify="center">
      <h1 class="section-title">Comparison</h1>
    </el-row>

    <el-row justify="center">
      <el-col :xs="32" :sm="32" :md="26" :lg="24" :xl="22">
        <el-row justify="center" :gutter="20">
          <el-col :xs="32" :sm="32" :md="20" :lg="20" :xl="20">
            
            <!-- 选择框放在图像上方 -->
            <el-row justify="center">
              <el-select
                class="select"
                v-model="value1"
                placeholder="Select"
                size="large"
                @change="handleChange1"
              >
                <el-option
                  v-for="item in options"
                  :key="item"
                  :label="item"
                  :value="item"/>
              </el-select>
            </el-row>

            <div class="demo-image">
              <div class="block">
                <el-skeleton
                  style="width: 100%"
                  :loading="comparison1Loading"
                  animated
                  :throttle="1000"
                >
                  <template #template>
                    <el-skeleton-item variant="image" style="width: 100%; height: 100%" />
                  </template>
                  <template #default>
                    <el-image :src="comparison1ImageRootPath" style="width: 100%; height: auto;" fit="contain"/>
                  </template>
                </el-skeleton>
                <span class="demonstration">input: {{ comparison1ImageRootPath }}</span>
              </div>
            </div>

          </el-col>
        </el-row>
      </el-col>
    </el-row>

  </div>
</template>

<style scoped>
.select {
  padding-top: 10px;
  width: 30%;
}

/* 路径文字居中 */
.demo-image .block {
  padding: 10px 0;
  text-align: center;
  display: inline-block;
  width: 100%;
  box-sizing: border-box;
  vertical-align: top;
}

/* 路径文字颜色 */
.demo-image .demonstration {
  padding-top: 10px;
  display: block;
  color: var(--el-text-color-secondary);
  word-wrap: break-word;
}

/* 调整标题和选择框的字体大小，使其与图片配合得更协调 */
.section-title {
  font-size: 2rem;  /* 增大标题字体 */
  margin-bottom: 20px;
}
</style>
