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
/* 隐藏点赞 */
/* 引用链接隐藏外部提示 */
.tk-action .tk-action-link:first-child,
.tag-link-tips {
    display: none!important;
}

/* 手机端搜索栏样式 */
@media screen and (max-width: 768px), (max-height: 580px) {
    .search-dialog {
        top: 2rem!important;
        left: 5%!important;
        width: 90%!important;
        height: auto!important;
        border-radius: 10px!important;
    }
}

/* 首页文章的标签位置 */
#recent-posts > .recent-post-item > .recent-post-info > .article-meta-wrap {
    bottom: 15px!important;
}

/* 优化关于界面人生图片 */
img.author-content-img.no-lightbox.entered.loaded {
    filter: blur(0) brightness(.8);
}

/* 轮播下面导航栏分类优化 */
#catalog-list,
anzhiyu.barrageContent {
    scrollbar-width: none;
}

/* 优化文章顶部分类和标签显示异常 */
#post-firstinfo .meta-firstline span.post-meta-categories a.post-meta-categories {
    background: rgb(107 107 107 / 50%)!important;
}

#post #post-info #post-firstinfo .meta-firstline .article-meta__tags {
    color: #888!important;
}

/* 优化手机端文章页面边角露底色 */
@media screen and (max-width: 768px) {
    .post .layout#content-inner {
        background: transparent;
    }
}

/* 代码块的边框显示优化 */
#article-container figure.highlight {
    border: var(--style-border);
}

/* 手机端nav栏 */
#sidebar #sidebar-menus {
    padding-top: 10px!important;
}

/* 擦亮效果 */
#recent-posts > .recent-post-item:not(a)::before {
    content: "";
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 200%;
    background: linear-gradient(to right, transparent, white, transparent);
    transform: translateX(-200%);
    transition: transform 0.5s linear;
    z-index: 1;
}

#recent-posts > .recent-post-item:not(a):hover::before {
    transform: translateX(100%) skewX(-60deg);
}

/* Twikoo*/
/* 评论框背景图优化 */
.twikoo .el-input__inner,
.twikoo .el-textarea__inner {
    transition: background-position-y 0.3s ease-in-out 0s !important;
}

.twikoo .el-input__inner:focus,
.twikoo .el-textarea__inner:focus {
    background-position-y: 350px;
}

.tk-input .el-textarea__inner {
    -moz-background-size: contain;
    -webkit-background-size: contain;
    -moz-background-size: contain;
    background-size: contain
}

/* 评论回复 */
.tk-action-link {
    border-radius: 10px;
    padding: 5px 10px 5px 10px;
    border: var(--style-border);
}

.tk-action-link:hover {
    background: var(--anzhiyu-theme);
    color: #fff;
}

/* 评论后台优化 */
#body-wrap.page .el-input__inner {
    background: #ffffff0f;
}

[data-theme=dark] details > summary {
    background: none!important;
}
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