<template>
  <div>
    <h1>BUG复现</h1>
    <div>所有选择项都会混合在一起</div>
    <div>
      <el-select v-model="A" class="m-2" placeholder="A">
        <el-option v-for="item in As" :key="item.value" :label="item.label" :value="item.value" />
      </el-select>
      <el-select v-model="B" class="m-2" placeholder="B">
        <el-option v-for="item in Bs" :key="item.value" :label="item.label" :value="item.value" />
      </el-select>
      <el-select v-model="C" class="m-2" placeholder="C">
        <el-option v-for="item in Cs" :key="item.value" :label="item.label" :value="item.value" />
      </el-select>
    </div>
    <div>只会显示第一个选中的tooltip</div>
    <div>
      <el-tooltip class="box-item" effect="dark" content="A" placement="top-start">
        <el-button>A</el-button>
      </el-tooltip>
      <el-tooltip class="box-item" effect="dark" content="B" placement="top-start">
        <el-button>B</el-button>
      </el-tooltip>
      <el-tooltip class="box-item" effect="dark" content="C" placement="top-start">
        <el-button>C</el-button>
      </el-tooltip>
    </div>
    <div>报错信息</div>
    <div>
      <div>
        Unhandled error during execution of scheduler flush. This is likely a Vue internals bug. Please open an issue at
        https://new-issue.vuejs.org/?repo=vuejs/core
      </div>
      <div>
        at &lt;BaseTransitiononAfterLeave=fn&lt;onTransitionLeave&gt;onBeforeEnter=fn&lt;onBeforeEnter&gt;onAfterEnter=fn&lt;onAfterShow&gt;... &gt;
      </div>
      <div>
        at &lt;Transition name="el-fade-in-linear"onAfterLeave=fn&lt;onTransitionLeave&gt;onBeforeEnter=fn&lt;onBeforeEnter&gt;... &gt;
      </div>
      <div>
        at &lt;ElTooltipContent ref="contentRef" aria-label=undefined boundaries-padding=0 ... &gt;
      </div>
      <div>
        at &lt;ElPopperRoot ref="popperRef" role="tooltip" class="box-item" &gt;
      </div>
      <div>
        at &lt;ElTooltip class="box-item" effect="dark" content="C" ... &gt;
      </div>
    </div>
  </div>
</template>
<script lang="ts" setup>
import { ID_INJECTION_KEY } from 'element-plus';
import { ElSelect,ElOption,ElTooltip,ElButton } from 'element-plus';
provide(ID_INJECTION_KEY, {
  prefix: 100,
  current: 0,
})
const A = ref('');
const B = ref('');
const C = ref('');

const As = reactive([
  {
    value: 'A1',
    label: 'A1',
  },
  {
    value: 'A2',
    label: 'A2',
  },
  {
    value: 'A3',
    label: 'A3',
  },
  {
    value: 'A4',
    label: 'A4',
  },
  {
    value: 'A5',
    label: 'A5',
  },
])
const Bs = reactive([
  {
    value: 'B1',
    label: 'B1',
  },
  {
    value: 'B2',
    label: 'B2',
  },
  {
    value: 'B3',
    label: 'B3',
  },
  {
    value: 'B4',
    label: 'B4',
  },
  {
    value: 'B5',
    label: 'B5',
  },
])
const Cs = reactive([
  {
    value: 'C1',
    label: 'C1',
  },
  {
    value: 'C2',
    label: 'C2',
  },
  {
    value: 'C3',
    label: 'C3',
  },
  {
    value: 'C4',
    label: 'C4',
  },
  {
    value: 'C5',
    label: 'C5',
  },
])
</script>
