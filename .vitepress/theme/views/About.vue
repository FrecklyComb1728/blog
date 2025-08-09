<template>
  <div class="about">
    <h1 class="title">关于本站</h1>
    <div class="about-content" style="grid-template-columns: 3fr 2fr">
      <!-- 介绍 -->
      <div class="about-item hello">
        <span class="text1">你好，很高兴认识你👋</span>
        <span class="text2 title2">我是 池鱼</span>
        <span class="text3">是一名 正在HRT的MtF🏳‍⚧🏳‍⚧</span>
      </div>
      <!-- 追求 -->
      <!--
      <div class="about-item pursuit">
        <span class="tip">#</span>
        <span class="title2">#</span>
        <span class="title2">#</span>
        <span class="title2">#</span>
      </div>
    </div>
    <div class="about-content" style="grid-template-columns: 2fr 3fr">
      -->
      <!-- 技能 -->

      <div class="about-item skills">
        <span class="tip">技能</span>
        <span class="title2">我不会的玩意</span>
        <div class="skills-list">
          <a
            v-for="(item, index) in skillsData"
            :key="index"
            :style="{ '--color': item.color }"
            :href="item.link"
            class="skills-item"
            target="_blank"
          >
            <div class="skills-logo">
              <i :class="`iconfont icon-${item.icon}`"></i>
            </div>
            <span class="skills-name">{{ item.name }}</span>
          </a>
        </div>
      </div>

      <!-- 生涯 -->
       <!--
      <div class="about-item career">
        <span class="tip">生涯</span>
        <span class="title2">
          <i>無限進步</i>
        </span>
        <div class="list">
          <span class="list-item" style="--color: #357ef5">#</span>
          <span class="list-item" style="--color: #eb372a">#</span>
        </div>
        <img
          class="career-img"
          src="https://pic.efefee.cn/uploads/2024/02/22/65d71db18bcf9.png"
          alt="career"
        />
      </div>
    </div>
    <div class="about-content" style="grid-template-columns: 3fr 2fr">
      -->
      <!-- 性格 -->
       <!--
      <div class="about-item character" style="--color: #4298b4">
        <span class="tip">#</span>
        <span class="title2">#</span>
        <span class="title2" style="color: var(--color)">#</span>
        <span class="more">
          在
          <a href="#" target="_blank">16personalities</a>
          了解更多关于
          <a href="#" target="_blank">
            #
          </a>
        </span>
        <img
          src="#"
          alt="male"
          class="male"
        />
      </div>
    -->
      <!-- 座右铭 -->
      <!--
      <div class="about-item">
        <span class="tip">#</span>
        <span class="title1" style="margin-top: 20px">#，</span>
        <span class="title2">#。</span>
      </div>
    </div>
    <div class="about-content" style="grid-template-columns: 1fr 1fr">
      <div
        class="about-item like image"
        style="
          --color: #0c0e20;
          background-image: url(#);
        "
      >
        <div class="image-content">
          <span class="tip">#</span>
          <span class="title2">#</span>
          <div class="image-desc">
            <span class="left">#</span>
          </div>
        </div>
      </div>
      <div
        class="about-item like image"
        style="
          --color: #7b3c25;
          background-image: url(#);
        "
      >
        <div class="image-content">
          <span class="tip">#</span>
          <span class="title2">#</span>
          <div class="image-desc">
            <span class="left">#</span>
          </div>
        </div>
      </div>
    </div>
    <div class="about-content" style="grid-template-columns: 2fr 3fr">
    -->
      <!-- 数据 -->

      <div
        class="about-item static image"
        style="
          --color: #0f1114;
          background-image: url(#);
        "
      >
        <div class="image-content">
          <span class="tip">数据</span>
          <span class="title2">访问统计</span>
          <div class="static-data">
            <div v-for="(item, key, index) in statisticsData" :key="index" class="static-item">
              <span class="static-name">{{ key }}</span>
              <span class="static-num">{{ item }}</span>
            </div>
          </div>
          <div class="image-desc opacity">
            <span class="left">
              统计信息来自 <a href="https://v6.51.la/" target="_blank">51la</a>
            </span>
          </div>
        </div>
      </div>

      <!-- 信息 -->
      <div class="about-item child">
        <div
          class="about-item map image"
          style="background-image: url(../images/maoming.png)"
        >
          <span class="position">我现在住在 <strong>中国，广东省，茂名市</strong></span>
        </div>
        <div class="about-itsem info">
          <div class="info-item">
            <span class="info-name">诞生于</span>
            <span class="info-num" style="--color: #43a6c6">2011</span>
          </div>
          <div class="info-item">
            <span class="info-name">生日</span>
            <span class="info-num" style="--color: #dfac46">0805</span>
          </div>
        </div>
      </div>
    </div>
    <!-- 心路历程 -->
    <div class="about-content" style="display: flex">
      <div class="about-item">
        <span class="tip">关于这个破站</span>
        <span class="title2">一个记录自己生活的站点？</span>
        <p class="text">
          这里我引用《DayLight》末尾独白：<br>
          <strong @click="playAudio" class="clickable-text">Knowing that I was going to get better and looking forward to a time that I would feel good again, helped me to keep moving forward, and sometimes I had to be brave ,and it wasn't always easy sometimes I faltered, I had bad days But I realized that being brave isn't supposed to be easy, as for me I feel it's the key way to keep moving forward.</strong>
        <br>—— Sam Berns</p>
        
      <!-- </div> -->
    <!-- </div> -->
    
    <!-- 隐私协议部分 -->
    <div id="Code_of_Conduct">
      <!-- <div class="about-item"> -->
        <p class="text">
          我爱你们。
        </p>
        <p> </p>
        <h2>隐私协议</h2>
        <p>本网站是一个静态网站，这意味着：</p>
        <ul>
          <li>我们不会在服务器端存储您的个人信息</li>
          <li>网站内容是预先生成的，不会动态处理用户数据</li>
          <li>我们不会主动收集或存储您的个人信息</li>
        </ul>
        
        <h3>第三方服务</h3>
        <p>尽管本网站本身是静态的，但我们使用了以下第三方服务，这些服务可能会收集和处理您的信息：</p>
        
        <h4>CDN 和托管服务</h4>
        <p>根据您访问的节点不同，以下服务提供商可能会收集您的信息：</p>
        
        <p><strong>Cloudflare</strong></p>
        <ul>
          <li>可能收集的信息：IP 地址、访问时间、请求的页面、浏览器信息</li>
          <li>用途：提供 CDN 服务、安全防护、性能优化</li>
          <li>隐私政策：<a href="https://www.cloudflare.com/privacypolicy/" target="_blank">Cloudflare 隐私政策</a></li>
        </ul>
        
        <p><strong>Netlify</strong></p>
        <ul>
          <li>可能收集的信息：IP 地址、访问日志、性能数据</li>
          <li>用途：网站托管、部署服务</li>
          <li>隐私政策：<a href="https://www.netlify.com/privacy/" target="_blank">Netlify 隐私政策</a></li>
        </ul>
        
        <h4>分析和统计服务</h4>
        
        <p><strong>百度统计</strong></p>
        <ul>
          <li>可能收集的信息：访问页面、访问时间、地理位置、设备信息、浏览器信息</li>
          <li>用途：网站流量分析、用户行为分析</li>
          <li>隐私政策：<a href="https://tongji.baidu.com/web/help/article?id=330" target="_blank">百度统计隐私政策</a></li>
        </ul>
        
        <p><strong>Google Analytics（谷歌分析）</strong></p>
        <ul>
          <li>可能收集的信息：匿名化的用户数据、页面浏览量、会话时长、地理位置</li>
          <li>用途：网站性能分析、用户行为分析</li>
          <li>隐私政策：<a href="https://policies.google.com/privacy" target="_blank">Google 隐私政策</a></li>
        </ul>
        
        <p><strong>Google Ads（谷歌广告）</strong></p>
        <ul>
          <li>可能收集的信息：广告展示数据、点击数据、用户兴趣信息</li>
          <li>用途：展示相关广告、广告效果分析</li>
          <li>隐私政策：<a href="https://policies.google.com/technologies/ads" target="_blank">Google 广告隐私政策</a></li>
        </ul>
        
        <p><strong>Umami 分析</strong></p>
        <ul>
          <li>可能收集的信息：页面浏览量、访问来源、设备类型（匿名化处理）</li>
          <li>用途：网站流量统计和分析</li>
          <li>特点：注重隐私保护，不使用 Cookie，数据匿名化处理</li>
          <li>实时查看：您可以在网站导航栏中实时查看站点流量统计</li>
        </ul>
        
        <h3>Cookie 和本地存储</h3>
        <p>我们的网站可能使用以下技术：</p>
        <ul>
          <li><strong>Cookie</strong>：用于网站功能和第三方服务</li>
          <li><strong>本地存储</strong>：用于保存用户偏好设置（如主题选择）</li>
          <li><strong>会话存储</strong>：用于临时存储页面状态</li>
        </ul>
        
        <h3>您的权利</h3>
        <p>您有权：</p>
        <ul>
          <li>了解我们收集的信息类型</li>
          <li>要求删除您的个人信息（如适用）</li>
          <li>选择退出某些数据收集</li>
          <li>禁用 Cookie 和 JavaScript（可能影响网站功能）</li>
        </ul>
        
        <h3>如何保护您的隐私</h3>
        <p>您可以通过以下方式保护您的隐私：</p>
        <ul>
          <li>使用隐私浏览模式</li>
          <li>禁用第三方 Cookie</li>
          <li>使用广告拦截器</li>
          <li>使用 VPN 服务</li>
          <li>定期清理浏览器数据</li>
        </ul>
        <h3>数据安全</h3>
        <p>虽然我们不直接收集您的个人信息，但我们：</p>
        <ul>
          <li>使用 HTTPS 加密传输</li>
          <li>选择信誉良好的第三方服务提供商</li>
          <li>定期审查第三方服务的隐私政策</li>
        </ul>
        <h3>儿童隐私</h3>
        <p>我们的网站不专门针对 14 岁以下的儿童。我们不会故意收集 14 岁以下儿童的个人信息。</p>       
        <h3>隐私政策更新</h3>
        <p>我们可能会不时更新本隐私政策。任何更改都会在此页面上发布，重大更改会通过网站公告通知用户。</p>
        <h3>联系我们</h3>
        <p>如果您对本隐私政策有任何疑问或关注，请通过以下方式联系我们：</p>
        <ul>
          <li>通过网站联系页面</li>
          <li>发送邮件至网站管理员</li>
        </ul>
        <h3>滥用与版权举报</h3>
        <p>如果您发现网站内容存在滥用、侵权或其他违法违规行为，请通过以下方式联系我们：</p>
        <ul>
          <li><strong>邮箱</strong>：wdsjwyf@gmail.com</li>
          <li><strong>QQ</strong>：3979158171</li>
        </ul>
        <p>我们将认真对待每一个举报，并在收到举报后及时处理相关问题。</p>
        
        <h3>适用法律</h3>
        <p>本隐私政策受中华人民共和国法律管辖。我们努力遵守适用的数据保护法律法规。</p>
        
        <hr>
        
        <p><em>本隐私政策旨在透明地说明我们的数据处理实践。我们建议您定期查看本政策以了解任何更新。</em></p>
      </div>
    </div>
  </div>
    
    <!-- 隐藏的音频元素 -->
    <audio ref="audioPlayer" :src="audioSrc" preload="none"></audio>
  </div>
</template>

<script setup>
import { getStatistics } from "@/api";

const { theme } = useData();

// 音频相关
const audioPlayer = ref(null);
const audioSrc = "https://cdn.mfawa.top/file/Sam_Berns_Monologue.mp3";
const isPlaying = ref(false);

// 播放/暂停音频
const playAudio = () => {
  if (!audioPlayer.value) return;
  
  if (isPlaying.value) {
    audioPlayer.value.pause();
    isPlaying.value = false;
  } else {
    audioPlayer.value.play().catch(error => {
      console.error("音频播放失败:", error);
    });
    isPlaying.value = true;
    
    // 监听音频播放结束事件
    audioPlayer.value.onended = () => {
      isPlaying.value = false;
    };
  }
};

// 技能数据

const skillsData = [
  {
    name: "JavaScript",
    color: "#f1e05abd",
    icon: "javascript",
    link: "https://developer.mozilla.org/zh-CN/docs/Web/JavaScript",
  },
  {
    name: "HTML5",
    color: "#e34f26",
    icon: "html5",
    link: "https://developer.mozilla.org/zh-CN/docs/Web/HTML",
  },
  {
    name: "CSS3",
    color: "#563d7c",
    icon: "css3",
    link: "https://developer.mozilla.org/zh-CN/docs/Web/CSS",
  },
  // {
  //   name: "NUXT.js",
  //   color: "#41b883",
  //   icon: "nuxtjs",
  //   link: "https://nuxtjs.org/",
  // },
  {
    name: "React",
    color: "#149ECA",
    icon: "react",
    link: "https://zh-hans.reactjs.org/",
  },
  {
    name: "Docker",
    color: "#2496f2",
    icon: "docker",
    link: "https://www.docker.com/",
  },
  // {
  //   name: "Java",
  //   color: "#F05032",
  //   icon: "java",
  //   link: "https://java.com/",
  // },
  {
    name: "Photoshop",
    color: "#31A8FF",
    icon: "photoshop",
    link: "https://www.adobe.com/cn/lead/creativecloud/business.html",
  },
  {
    name: "ChatGPT",
    color: "#4AA181",
    icon: "chatgpt",
    link: "https://chat.openai.com/",
  },
];

// 站点统计数据
const statisticsData = ref(null);

// 获取站点统计数据
const getStatisticsData = async () => {
  const result = await getStatistics(theme.value.tongji["51la"]);
  statisticsData.value = result;
};

onMounted(() => {
  getStatisticsData();
});
</script>

<style lang="scss" scoped>
.about {
  .title {
    font-size: 2.4rem;
    text-align: center;
    border: none;
  }
  .about-content {
    display: grid;
    grid-template-columns: auto auto;
    gap: 20px;
    margin-bottom: 20px;
    .about-item {
      position: relative;
      display: flex;
      flex-direction: column;
      width: 100%;
      padding: 1.2rem 2rem;
      border-radius: 12px;
      background-color: var(--main-card-background);
      border: 1px solid var(--main-card-border);
      box-shadow: 0 8px 12px -4px var(--main-border-shadow);
      overflow: hidden;
      .tip {
        font-size: 14px;
        opacity: 0.8;
        margin-bottom: 12px;
      }
      .title1 {
        font-size: 36px;
        font-weight: bold;
        opacity: 0.6;
      }
      .title2 {
        font-size: 36px;
        font-weight: bold;
        margin-right: 4rem;
      }
      .text {
        font-size: 18px;
        margin: 0.6rem 0;
        
        .clickable-text {
          cursor: pointer;
          border-bottom: 1px dotted transparent;
          transition: color 0.3s, border-color 0.3s;
          
          &:hover {
            color: var(--main-color);
            border-bottom-color: var(--main-color);
          }
        }
      }
      &.child {
        background-color: transparent;
        border: none;
        box-shadow: none;
        padding: 0;
        gap: 20px;
        .about-item {
          height: 100%;
        }
      }
      &.hello {
        justify-content: center;
        padding: 2rem;
        color: #fff;
        background-image: linear-gradient(120deg, #5b27ff 0%, #00d4ff 100%);
        background-size: 200% 200%;
        animation: gradientFlow 6s ease infinite;
        .title2 {
          line-height: 2;
        }
      }
      &.pursuit {
        .title2 {
          line-height: 1.2;
          &:last-child {
            display: inline-block;
            background-size: 100% 100%;
            background-clip: text;
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-repeat: no-repeat;
            background-image: linear-gradient(45deg, #fa7671 50%, #f45f7f);
          }
        }
      }
      &.character {
        min-height: 220px;
        cursor: pointer;
        .more {
          margin-top: auto;
          font-size: 14px;
          color: var(--main-color-gray);
          a {
            color: var(--main-color-gray);
            &:hover {
              color: var(--color);
            }
          }
        }
        .male {
          position: absolute;
          top: 20px;
          right: -10px;
          height: 140%;
          width: auto;
          transition: transform 0.5s;
          transform-origin: top center;
          @media (max-width: 768px) {
            height: 80%;
          }
        }
        &:hover {
          .male {
            transform: scale(1.2);
          }
        }
      }
      &.skills {
        .skills-list {
          margin-top: 12px;
          display: flex;
          flex-direction: row;
          flex-wrap: wrap;
          .skills-item {
            display: flex;
            align-items: center;
            margin-right: 10px;
            margin-top: 10px;
            padding: 8px 12px 8px 8px;
            border-radius: 40px;
            background-color: var(--main-site-background);
            border: 1px solid var(--main-card-border);
            box-shadow: 0 8px 12px -4px var(--main-border-shadow);
            transition: background-color 0.3s;
            cursor: pointer;
            .skills-logo {
              display: flex;
              align-items: center;
              justify-content: center;
              width: 32px;
              height: 32px;
              margin-right: 8px;
              border-radius: 50%;
              background-color: var(--color);
              .iconfont {
                color: #fff;
              }
            }
            .skills-name {
              font-weight: bold;
              transition: color 0.3s;
            }
            &:hover {
              background-color: var(--main-card-background);
            }
          }
        }
      }
      &.career {
        .title2 {
          letter-spacing: 0.2rem;
          font-size: 40px;
        }
        .list {
          margin-top: 12px;
          display: flex;
          flex-direction: column;
          .list-item {
            display: flex;
            flex-direction: row;
            align-items: center;
            margin-bottom: 12px;
            color: var(--main-font-second-color);
            &::before {
              content: "";
              display: block;
              width: 16px;
              height: 16px;
              background-color: var(--color);
              border-radius: 50%;
              margin-right: 8px;
            }
          }
        }
        .career-img {
          position: absolute;
          bottom: -10px;
          left: 0;
          width: 100%;
          @media (max-width: 768px) {
            position: static;
          }
        }
      }
      &.game {
        min-height: 300px;
        @media (max-width: 768px) {
          min-height: 240px;
        }
      }
      &.like {
        min-height: 400px;
        @media (max-width: 768px) {
          min-height: 300px;
        }
      }
      &.image {
        background-position: center;
        background-size: cover;
        background-repeat: no-repeat;
        .image-content {
          flex-grow: 1;
          display: flex;
          flex-direction: column;
          z-index: 2;
          color: #fff;
          .image-desc {
            width: 100%;
            display: flex;
            flex-direction: row;
            align-items: center;
            justify-content: space-between;
            margin-top: auto;
            &.opacity {
              font-size: 14px;
              color: #eee;
              opacity: 0.8;
              a {
                color: #eee;
                &:hover {
                  color: var(--main-color);
                }
              }
            }
          }
        }
        &::after {
          content: "";
          position: absolute;
          width: 100%;
          height: 100%;
          top: 0;
          left: 0;
          box-shadow: inset 0 -70px 204px 10px var(--color);
          z-index: 0;
        }
      }
      &.static {
        .static-data {
          display: grid;
          gap: 12px;
          grid-template-columns: 1fr 1fr;
          margin: 20px 0;
          .static-item {
            display: flex;
            flex-direction: column;
            .static-name {
              font-size: 15px;
              opacity: 0.8;
            }
            .static-num {
              font-size: 34px;
              font-weight: bold;
            }
          }
        }
      }
      &.map {
        min-height: 170px;
        background-size: 100%;
        transition: background 1.5s ease-in-out;
        cursor: pointer;
        @media (max-width: 768px) {
          background-size: cover;
          pointer-events: none;
        }
        .position {
          display: block;
          position: absolute;
          left: 0;
          bottom: 0;
          width: 100%;
          padding: 20px 30px;
          color: #fff;
          background-color: #636352;
          font-size: 20px;
          transition: bottom 1s;
        }
        &:hover {
          background-size: 120%;
          background-position-x: 0;
          background-position-y: 36%;
          .position {
            bottom: -80px;
          }
        }
      }
      &.info {
        flex-direction: row;
        align-items: center;
        justify-content: flex-start;
        .info-item {
          display: flex;
          flex-direction: column;
          margin-right: 32px;
          .info-name {
            font-size: 14px;
            margin-bottom: 8px;
            color: var(--main-font-second-color);
          }
          .info-num {
            font-size: 34px;
            font-weight: bold;
            color: var(--color);
          }
        }
      }
    }
    &:last-child {
      margin-bottom: 0;
    }
    @media (max-width: 768px) {
      display: flex;
      flex-direction: column;
    }
  }
}
</style>