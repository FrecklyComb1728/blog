<template>
  <div ref="commentRef" id="comment-dom" :class="['comment-content', 'twikoo', { fill }]" />
</template>

<script setup>
import { jumpRedirect } from "@/utils/commonTools";
import initComments from "@/utils/initComments";

const props = defineProps({
  // 填充评论区
  fill: {
    type: [Boolean, String],
    default: false,
  },
});

const { theme } = useData();
const { comment } = theme.value;

// 评论数据
const twikoo = ref(null);
const commentRef = ref(null);

// 初始化 Twikoo
const initTwikoo = async () => {
  try {
    await nextTick();
    const Twikoo = await initComments(theme.value);
    twikoo.value = Twikoo.init({
      el: commentRef.value || "#comment-dom",
      envId: comment.twikoo.envId,
      onCommentLoaded: () => {
        console.log("评论已加载完毕");
        if (props.fill) fillComments(props.fill);
        jumpRedirect(null, theme.value, true);
      },
    });
    return twikoo.value;
  } catch (error) {
    console.error("初始化评论出错：", error);
  }
};

// 填充评论区
const fillComments = (data) => {
  console.log("填充评论：", data);
  // 获取评论元素
  const commentDom = document.querySelector(".tk-input.el-textarea");
  if (!commentDom) return false;
  // 获取输入框
  const commentInput = commentDom.querySelector("textarea");
  // 写入内容
  commentInput.value = data + "\n\n";
  commentInput.focus();
};

onMounted(() => {
  initTwikoo();
});
</script>

<style>
#twikoo .el-loading-mask {
    display: flex;
    align-items: center;
    justify-content: center;
}

#twikoo .el-loading-spinner {
    display: inline-flex;
    width: unset;
}

.el-textarea__inner {
    font-family: var(--main-font-family);
}

.tk-comments {
    color: var(--tk-text);
}

.tk-submit .tk-avatar {
    display: none
}

.tk-row .tk-col {
    flex-direction: column-reverse
}

.tk-row .tk-col .tk-input textarea {
    min-height: 150px!important;
    border-radius: var(--radius-large);
    padding: 1rem 1.5rem
}

.tk-row .tk-col .tk-input textarea:focus {
    border-color: var(--primary)
}

.tk-meta-input {
    position: relative;
    margin-top: .75rem
}

.tk-meta-input div {
    min-height: 2.5rem
}

.tk-meta-input div .el-input-group__prepend {
    border-top-left-radius: .5rem;
    border-bottom-left-radius: .5rem;
    background-color: inherit!important;
    min-height: inherit
}

.tk-meta-input div input {
    border-top-right-radius: .5rem;
    border-bottom-right-radius: .5rem;
    padding-left: 1rem;
    padding-right: 1rem
}

.tk-meta-input div input:focus {
    border-color: var(--primary)!important
}

.tk-meta-input div input {
    min-height: inherit
}

.tk-row.actions {
    margin-left: 0!important;
    margin-top: 0!important;
    width: 100%
}

.tk-row.actions .__markdown {
    display: none!important
}

.tk-row.actions .tk-preview,.tk-row.actions .tk-send,.tk-row.actions .tk-cancel {
    height: 2rem;
    border-radius: .5rem;
    border-style: none;
    background-color: var(--btn-regular-bg-active)!important;
    padding-left: .75rem;
    padding-right: .75rem;
    padding-top: 0;
    padding-bottom: 0;
    color: var(--btn-content)!important
}

.tk-row.actions .tk-preview:disabled,.tk-row.actions .tk-send:disabled,.tk-row.actions .tk-cancel:disabled {
    background-color: var(--btn-regular-bg)!important;
    color: #ffffffa1!important
}

.tk-comments-title .__comments svg {
    fill: var(--primary)
}

.tk-comment {
    border-radius: 1rem;
    border-width: 1px;
    border-color: #9093994f;
    padding: 1rem;
    transition-property: all;
    transition-timing-function: cubic-bezier(.4,0,.2,1);
    transition-duration: .15s
}

.tk-comment:hover {
    --tw-shadow: 0 4px 6px -1px rgb(0 0 0 / .1), 0 2px 4px -2px rgb(0 0 0 / .1);
    --tw-shadow-colored: 0 4px 6px -1px var(--tw-shadow-color), 0 2px 4px -2px var(--tw-shadow-color);
    box-shadow: var(--tw-ring-offset-shadow, 0 0 #0000),var(--tw-ring-shadow, 0 0 #0000),var(--tw-shadow)
}

.tk-comment .tk-action-icon svg {
    fill: var(--primary)
}

.tk-action .tk-action-count {
    color: var(--btn-content)
}

.tk-meta .tk-tag {
    border-radius: .5rem;
    border-style: none;
    color: var(--btn-content)
}

.tk-meta .tk-tag-green {
    background-color: var(--btn-regular-bg)
}

.tk-meta .tk-tag-green:is(.dark *) {
    background-color: var(--primary);
    color: var(--deep-text)
}

.tk-content img,.tk-preview-container img {
    display: inline;
    vertical-align: bottom!important
}

.tk-content a,.tk-preview-container a {
    font-weight: 500;
    color: var(--primary);
    text-decoration-line: underline
}

.tk-content .tk-ruser,.tk-preview-container .tk-ruser {
    text-decoration-line: none
}

.tk-content :not(pre)>code,.tk-preview-container :not(pre)>code {
    border-radius: .375rem;
    background-color: var(--inline-code-bg);
    padding: .125rem .25rem;
    font-weight: 600;
    color: var(--inline-code-color)
}

.tk-content li:before,.tk-preview-container li:before {
    color: var(--primary);
    --tw-content: "•";
    content: var(--tw-content)
}

.tk-replies .tk-comment {
    background-color: var(--page-bg)
}

.tk-replies .tk-comment .tk-content>span:first-of-type {
    font-size: .75rem;
    line-height: 1rem
}

.twikoo .code-block pre {
    border-radius: .75rem!important
}

.twikoo .code-block pre:not([class]) {
    overflow: auto;
    background-color: var(--codeblock-bg);
    padding: .5rem;
    color: var(--code-block-text)
}

.twikoo .code-block .copy-btn-icon {
    width: inherit!important;
    height: inherit!important
}

.tk-expand-wrap .tk-expand,.tk-collapse-wrap .tk-expand {
    margin-top: .25rem
}

.tk-expand-wrap .tk-expand:hover,.tk-collapse-wrap .tk-expand:hover {
    border-radius: .5rem;
    background-color: var(--btn-plain-bg-hover)
}

.card-base {
    overflow: visible
}

.tk-action-icon,.tk-owo,.tk-submit,.tk-cancel,.tk-preview,.tk-admin,.tk-delete,.tk-edit {
    cursor: pointer;
    transition: all .2s ease
}

.tk-action {
    min-height: 24px;
    display: flex;
    align-items: center
}

.tk-submit-wrapper {
    position: relative
}

.tk-admin-panel {
    position: relative;
    z-index: 100
}

:root {
    --radius-large: 1rem;
    --content-delay: .15s
}
</style>