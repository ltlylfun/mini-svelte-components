<script>
  // 主应用组件 - 展示所有组件的使用示例
  import Countdown from './lib/components/Countdown.svelte';
  import Modal from './lib/components/Modal.svelte';
  import Carousel from './lib/components/Carousel.svelte';
  import Tabs from './lib/components/Tabs.svelte';
  import Dropdown from './lib/components/Dropdown.svelte';
  import Tooltip from './lib/components/Tooltip.svelte';
  import Accordion from './lib/components/Accordion.svelte';
  import Toast from './lib/components/Toast.svelte';
  import ProgressBar from './lib/components/ProgressBar.svelte';
  import CheckboxGroup from './lib/components/CheckboxGroup.svelte';
  import Counter from './lib/components/Counter.svelte';

  // 状态管理
  let modalOpen = false;
  let countdown = 10;
  let toastMsg = '';
  let progress = 30;
  let checkedValues = [];
  let dropdownValue;

  // 标签页数据
  const tabs = [
    { label: "标签一", content: "<div>内容一</div>" },
    { label: "标签二", content: "<div>内容二</div>" },
    { label: "标签三", content: "<div>内容三</div>" }
  ];

  // 下拉菜单选项
  const dropdownOptions = [
    { label: "选项一", value: 1 },
    { label: "选项二", value: 2 },
    { label: "选项三", value: 3 }
  ];

  // 手风琴数据
  const accordionItems = [
    { title: "面板一", content: "<div>内容一</div>" },
    { title: "面板二", content: "<div>内容二</div>" },
    { title: "面板三", content: "<div>内容三</div>" }
  ];

  // 复选框选项
  const checkboxOptions = [
    { label: "选项A", value: "A" },
    { label: "选项B", value: "B" },
    { label: "选项C", value: "C" }
  ];
</script>

<main>
  <h1>Countdown 倒计时组件示例</h1>
  <input
    type="number"
    bind:value={countdown}
    min="0"
    style="width: 60px"
  />
  <Countdown seconds={countdown} />
  <hr />

  <h1>Modal 模态框组件示例</h1>
  <button on:click={() => modalOpen = true}>打开模态框</button>
  <Modal open={modalOpen} onClose={() => modalOpen = false}>
    <div>这是一个模态框内容</div>
  </Modal>
  <hr />

  <h1>Carousel 轮播图组件示例</h1>
  <Carousel />
  <hr />

  <h1>Tabs 标签页组件示例</h1>
  <Tabs {tabs} />
  <hr />

  <h1>Dropdown 下拉菜单组件示例</h1>
  <Dropdown
    options={dropdownOptions}
    value={dropdownValue}
    onChange={(value) => dropdownValue = value}
  />
  <div style="margin-top: 8px">当前选择：{dropdownValue || "无"}</div>
  <hr />

  <h1>Tooltip 气泡提示组件示例</h1>
  <Tooltip text="这是气泡提示">把鼠标移到我上面</Tooltip>
  <hr />

  <h1>Accordion 手风琴组件示例</h1>
  <Accordion items={accordionItems} />
  <hr />

  <h1>Toast 消息提示组件示例</h1>
  <button on:click={() => toastMsg = "操作成功！"}>显示 Toast</button>
  <Toast message={toastMsg} onClose={() => toastMsg = ""} />
  <hr />

  <h1>ProgressBar 进度条组件示例</h1>
  <input
    type="range"
    min="0"
    max="100"
    bind:value={progress}
  />
  <ProgressBar value={progress} max={100} />
  <hr />

  <h1>CheckboxGroup 复选框组组件示例</h1>
  <CheckboxGroup
    options={checkboxOptions}
    value={checkedValues}
    onChange={(newValue) => checkedValues = newValue}
  />
  <div>已选：{checkedValues.join(",") || "无"}</div>
  <hr />

  <h1>Counter 计数器组件示例</h1>
  <Counter initial={0} />
  <hr />
</main>
