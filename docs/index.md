<style>
  .homepage-background {
    position: relative;
    width: 100%;
    min-height: 100vh;
    background-image: url('https://s1.imagehub.cc/images/2025/04/19/d6c30e45726cbd71de5c13bc29d7d490.jpg');
    background-size: cover;
    background-position: center;
    display: flex;
    justify-content: center;
    align-items: center;
    text-align: center;
  }
  
  .homepage-background::after {
    content: '';
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: rgba(0, 0, 0, 0.4); /* 改为深色遮罩增强文字对比度 */
    z-index: 1;
  }
  
  .welcome-content {
    position: relative;
    z-index: 2;
    max-width: 80%;
    padding: 2rem;
  }
  
  .welcome-content h1 {
    font-family: 'Montserrat', 'Microsoft YaHei', sans-serif;
    font-size: 3.5rem;
    font-weight: 700;
    letter-spacing: 3px;
    line-height: 1.3;
    margin-bottom: 1.5rem;
    color: #fff;
    text-shadow: 0 2px 10px rgba(0, 0, 0, 0.6);
    background: linear-gradient(to right, #fff, #f3f3f3);
    -webkit-background-clip: text;
    background-clip: text;
    -webkit-text-fill-color: transparent;
    animation: fadeIn 1.5s ease, glow 2s infinite alternate;
  }
  
  @keyframes fadeIn {
    from { opacity: 0; transform: translateY(20px); }
    to { opacity: 1; transform: translateY(0); }
  }
  
  @keyframes glow {
    from { text-shadow: 0 0 5px #fff, 0 0 10px rgba(255, 255, 255, 0.5); }
    to { text-shadow: 0 0 10px #fff, 0 0 20px rgba(255, 255, 255, 0.8); }
  }
  
  @media (max-width: 768px) {
    .welcome-content h1 {
      font-size: 2.2rem;
      letter-spacing: 1px;
    }
  }
</style>

<div class="homepage-background">
  <div class="welcome-content">
    <h1>欢迎来到我的网站</h1>
  </div>
</div>