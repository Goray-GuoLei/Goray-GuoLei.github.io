<style>
  /* 重置默认边距 */
  body, html {
    margin: 0;
    padding: 0;
    width: 100%;
    height: 100%;
  }

  /* 全屏背景容器 */
  .fullpage-background {
    position: fixed; /* 使用 fixed 定位确保覆盖整个视口 */
    top: 0;
    left: 0;
    width: 100vw;
    height: 100vh;
    background-image: url('https://s1.imagehub.cc/images/2025/04/19/d6c30e45726cbd71de5c13bc29d7d490.jpg');
    background-size: cover;
    background-position: center;
    background-repeat: no-repeat;
    z-index: -1; /* 置于内容下层 */
  }

  /* 半透明渐变遮罩 */
  .fullpage-background::after {
    content: '';
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: linear-gradient(135deg, rgba(0,0,0,0.4) 0%, rgba(0,0,0,0.2) 100%);
  }

  /* 内容容器 */
  .hero-content {
    position: relative;
    min-height: 100vh;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    text-align: center;
    padding: 2rem;
    box-sizing: border-box;
  }

  /* 标题样式 */
  .hero-title {
    font-family: 'Montserrat', 'Microsoft YaHei', sans-serif;
    font-size: 3.5rem;
    font-weight: 700;
    letter-spacing: 3px;
    line-height: 1.3;
    color: #fff;
    margin-bottom: 1.5rem;
    text-shadow: 0 2px 10px rgba(0, 0, 0, 0.6);
    background: linear-gradient(to right, #fff, #f3f3f3);
    -webkit-background-clip: text;
    background-clip: text;
    -webkit-text-fill-color: transparent;
    animation: fadeIn 1.5s ease;
  }

  /* 副标题样式 */
  .hero-subtitle {
    font-family: 'Montserrat', 'Microsoft YaHei', sans-serif;
    font-size: 1.5rem;
    font-weight: 300;
    color: rgba(255, 255, 255, 0.9);
    max-width: 800px;
    margin: 0 auto;
    text-shadow: 0 1px 3px rgba(0, 0, 0, 0.5);
  }

  /* 动画效果 */
  @keyframes fadeIn {
    from { opacity: 0; transform: translateY(20px); }
    to { opacity: 1; transform: translateY(0); }
  }

  /* 响应式调整 */
  @media (max-width: 768px) {
    .hero-title {
      font-size: 2.2rem;
      letter-spacing: 1px;
    }
    .hero-subtitle {
      font-size: 1.2rem;
    }
  }
</style>

<!-- 背景层 -->
<div class="fullpage-background"></div>

<!-- 内容层 -->
<div class="hero-content">
  <h1 class="hero-title">欢迎来到我的网站</h1>
  <p class="hero-subtitle">探索更多精彩内容</p>
</div>