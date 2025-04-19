<style>
  /* 重置默认边距 */
  body, html {
    margin: 0;
    padding: 0;
    width: 100%;
    height: 100%;
    overflow: hidden; /* 防止加载时滚动 */
  }

  /* 加载动画容器 */
  .loader {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: #000;
    display: flex;
    justify-content: center;
    align-items: center;
    z-index: 1000;
    transition: opacity 0.5s ease;
  }

  /* 加载动画 */
  .loader-spinner {
    width: 50px;
    height: 50px;
    border: 5px solid rgba(255, 255, 255, 0.3);
    border-radius: 50%;
    border-top-color: #fff;
    animation: spin 1s ease-in-out infinite;
  }

  @keyframes spin {
    to { transform: rotate(360deg); }
  }

  /* 全屏背景容器 */
  .fullpage-background {
    position: fixed;
    top: 0;
    left: 0;
    width: 100vw;
    height: 100vh;
    background-image: url('https://s1.imagehub.cc/images/2025/04/19/d6c30e45726cbd71de5c13bc29d7d490.jpg');
    background-size: cover;
    background-position: center;
    background-repeat: no-repeat;
    z-index: -1;
    opacity: 0;
    transition: opacity 1s ease;
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
    opacity: 0;
    transform: translateY(20px);
    transition: opacity 0.8s ease, transform 0.8s ease;
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

  /* 加载完成后的样式 */
  body.loaded .fullpage-background {
    opacity: 1;
  }

  body.loaded .hero-content {
    opacity: 1;
    transform: translateY(0);
  }

  body.loaded .loader {
    opacity: 0;
    pointer-events: none;
  }
</style>

<!-- 加载层 -->
<div class="loader">
  <div class="loader-spinner"></div>
</div>

<!-- 背景层 -->
<div class="fullpage-background"></div>

<!-- 内容层 -->
<div class="hero-content">
  <h1 class="hero-title">欢迎来到我的网站</h1>
  <p class="hero-subtitle">探索更多精彩内容</p>
</div>

<script>
  // 确保所有资源加载完成
  window.addEventListener('load', function() {
    // 添加延迟确保加载动画可见
    setTimeout(function() {
      document.body.classList.add('loaded');
      
      // 加载完成后移除加载器（可选）
      setTimeout(function() {
        const loader = document.querySelector('.loader');
        if (loader) loader.remove();
        document.body.style.overflow = 'auto';
      }, 500); // 与过渡时间匹配
    }, 500);
  });

  // 预加载背景图片
  const img = new Image();
  img.src = 'https://s1.imagehub.cc/images/2025/04/19/d6c30e45726cbd71de5c13bc29d7d490.jpg';
</script>