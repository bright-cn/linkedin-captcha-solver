# LinkedIn 验证码解决方案

[![推广](https://github.com/bright-cn/LinkedIn-Scraper/raw/main/Proxies%20and%20scrapers%20GitHub%20bonus%20banner.png)](https://www.bright.cn/products/web-unlocker/captcha-solver/linkedin)

使用 Bright Data 先进的验证码解决技术轻松绕过 LinkedIn 验证码。通过机器学习算法、[自动 IP 轮换](https://www.bright.cnsolutions/rotating-proxies)以及强大的代理基础设施，确保对目标网站的无缝持续访问。

Bright Data 的 CAPTCHA Solver 是 [**抓取浏览器**](https://www.bright.cn/products/scraping-browser) 和 [**网页解锁工具 API**](https://www.bright.cn/products/web-unlocker) 内置的一项功能，可完整应对各种复杂的验证码挑战。

## 功能亮点  
- **高速验证码破解**：自动且准确地解决 LinkedIn 验证码，处理速度快。  
- **IP 轮换**：通过自动重试与动态 IP 调整，避免被封禁。  
- **浏览器指纹仿真**：模拟真实用户行为，[绕过复杂的机器人检测](https://www.bright.cn/blog/web-data/anti-scraping-techniques)。  
- **JavaScript 渲染**：可处理大量 JavaScript 动态内容的网站。  
- **全球区域覆盖**：精准定位全球各地区，解锁对应内容。  
- **无缝集成**：轻松结合 Puppeteer、Playwright 和 Selenium 等工具使用。  
- **事件监控**：追踪验证码处理事件，如检测、成功或失败。

## 为什么选择 LinkedIn 验证码解决方案

### **全球 20,000+ 客户的信赖**  
Bright Data 的 CAPTCHA Solver 拥有开发者、企业及各类规模客户的信任，可靠性和性能均属顶尖。

### **依托高质量代理网络**  
凭借超过 1 亿 IP 及先进的地理定位功能，我们的代理基础设施可确保流畅、不断线的验证码破解。

### **AI 驱动的验证码破解**  
我们的验证码解决方案利用先进的 AI 逻辑来自动检测、分析并完成验证码处理。它可处理重试、指纹伪装和请求头调整，能绕过最为复杂的反机器人措施。

### **为开发者而生**  
- 与 Puppeteer、Playwright、Selenium 等工具轻松整合。  
- 验证码处理逻辑可自由定制。  
- 自动重试与动态 IP 切换，保障采集过程不中断。

> **小贴士 💡**  
>> 已经拥有验证码处理方案？可结合我们针对 [Puppeteer](https://www.bright.cn/integration/puppeteer)、[Playwright](https://www.bright.cn/integration/playwright) 和 [Selenium](https://www.bright.cn/integration/selenium) 的代理服务，显著减少验证码触发率。

## 工作原理

Bright Data 的 CAPTCHA Solver 已集成于 **抓取浏览器** 和 **网页解锁工具**，让验证码处理变得轻而易举。

### **自动化验证码解决**  
验证码 Solver 会实时检测并自动解决验证码。只需启用该功能，检测到验证码后即可自动完成处理。

### **针对 LinkedIn 验证码的自定义选项**  
```javascript
// 为不同 CAPTCHA 类型定义默认选项
function getCaptchaOptions(captchaType, customOptions = {}) {
  const defaultOptions = {
    timeout: 30000, // 等待验证码解决的最长时间（毫秒）
    check_timeout: 500, // 查询验证码状态的时间间隔（毫秒）
    wait_networkidle: { timeout: 1000 }, // 等待网络空闲 1 秒
    debug: false // 调试模式（默认关闭）
  };

  // 定义各类 CAPTCHA 的选择器
  const captchaSelectors = {
    DataDome: { selector: '#datadome-captcha', success_selector: '#captcha-success' },
    reCAPTCHA: { selector: '.g-recaptcha', success_selector: '.recaptcha-success' },
    ClickCaptcha: { selector: '.click-captcha', success_selector: '.captcha-passed' },
    hCaptcha: { selector: '.h-captcha', success_selector: '.hcaptcha-success' },
    PerimeterX: { selector: '#px-captcha', success_selector: '#px-success' },
    SimpleCaptcha: { selector: '.simple-captcha', success_selector: '.captcha-done' },
    FunCaptcha: { selector: '.funcaptcha', success_selector: '.funcaptcha-success' },
    CloudflareTurnstile: { selector: '.cf-turnstile', success_selector: '.cf-success' },
    AWSWAF: { selector: '#aws-waf-captcha', success_selector: '#aws-waf-success' },
    GeeTest: { selector: '.geetest-captcha', success_selector: '.geetest-success' },
    KeyCAPTCHA: { selector: '#keycaptcha', success_selector: '#keycaptcha-success' },
    PuzzleCAPTCHA: { selector: '.puzzle-captcha', success_selector: '.puzzle-solved' },
    YandexCAPTCHA: { selector: '#yandex-captcha', success_selector: '#yandex-success' },
    ImageCAPTCHA: { selector: '.image-captcha', success_selector: '.image-captcha-success' },
    TextCAPTCHA: { selector: '.text-captcha', success_selector: '.text-captcha-success' }
  };

  // 为指定类型的 CAPTCHA 获取相应的选择器选项
  const selectedOptions = captchaSelectors[captchaType] || {};

  // 将默认选项、CAPTCHA 类型专属选项，以及任何自定义覆盖融合
  return { ...defaultOptions, ...selectedOptions, ...customOptions };
}

// 不同 CAPTCHA 类型的示例用法
const ddOptions = getCaptchaOptions('DataDome', { timeout: 40000, debug: true });
const recaptchaOptions = getCaptchaOptions('reCAPTCHA', { debug: true });
const hcaptchaOptions = getCaptchaOptions('hCaptcha');

console.log(ddOptions);
console.log(recaptchaOptions);
console.log(hcaptchaOptions);

// 示例错误处理
try {
  if (!document.querySelector(ddOptions.selector)) {
    throw new Error(`未找到对应的 CAPTCHA 元素，selector: ${ddOptions.selector}`);
  }

  // 在这里编写你的验证码解决逻辑
  solveCaptcha(ddOptions);
} catch (error) {
  console.error('无法解决验证码：', error.message);
}
```

#### 示例工作流程：  
1. **检测验证码**：识别验证码类型（如 PerimeterX）。  
2. **解决验证码**：使用 AI 逻辑，自动完成验证码解析。  
3. **失败重试**：若失败，会使用新 IP 自动重试。  
4. **返回结果**：验证码通过后，系统将提供无障碍访问目标网站。

## 支持的验证码类型

Bright Data 的 CAPTCHA Solver 支持多种验证码类型，包括：

- [**DataDome**](https://www.bright.cn/products/web-unlocker/captcha-solver/datadome)
- [**reCAPTCHA**](https://www.bright.cn/products/web-unlocker/captcha-solver/recaptcha)
- [**Click Captcha**](https://www.bright.cn/products/web-unlocker/captcha-solver/click-captcha)
- [**Cloudflare**](https://www.bright.cn/products/web-unlocker/captcha-solver/Cloudflare)
- [**PerimeterX**](https://www.bright.cn/products/web-unlocker/captcha-solver/perimeterx)
- [**SimpleCaptcha**](https://www.bright.cn/products/web-unlocker/captcha-solver/simplecaptcha)
- [**FunCaptcha**](https://www.bright.cn/products/web-unlocker/captcha-solver/funcaptcha)
- [**Cloudflare Turnstile**](https://www.bright.cn/products/web-unlocker/captcha-solver/cloudflare-turnstile)
- [**AWS WAF Captcha**](https://www.bright.cn/products/web-unlocker/captcha-solver/aws-waf-captcha)
- [**GeeTest CAPTCHA**](https://www.bright.cn/products/web-unlocker/captcha-solver/geetest-captcha)
- [**KeyCAPTCHA**](https://www.bright.cn/products/web-unlocker/captcha-solver/keycaptcha)
- [**Puzzle CAPTCHA**](https://www.bright.cn/products/web-unlocker/captcha-solver/puzzle-captcha)
- [**Yandex CAPTCHA**](https://www.bright.cn/products/web-unlocker/captcha-solver/yandex-captcha)
- [**Image CAPTCHA**](https://www.bright.cn/products/web-unlocker/captcha-solver/image-captcha)
- [**Text CAPTCHA**](https://www.bright.cn/products/web-unlocker/captcha-solver/text-captcha)

## 高级自定义

[Bright Data 的 CAPTCHA Solver](https://github.com/bright-cn/Captcha-solver) 支持深度自定义，可根据不同场景微调验证码解决逻辑。

## **事件监控**  
您可以追踪验证码解决事件，以便处理更高级的使用场景：  
- `Captcha.detected`：检测到验证码并开始求解。  
- `Captcha.solveFinished`：验证码成功解决。  
- `Captcha.solveFailed`：验证码解决失败。

## **价格方案**

| **方案**            | **价格 (每 1K 结果)** | **月度费用**    | **描述**                                      |  
|---------------------|-----------------------|----------------|------------------------------------------------|  
| **按使用量付费**    | $1.50                | 无月度承诺     | 适用于临时或小规模爬取需求。                       |  
| **增长型（Growth）**| $1.27                | $499           | 为需要扩展功能的团队定制。                          |  
| **商业版（Business）**| $1.12                | $999           | 适用于大规模爬取任务。                               |  
| **高级版（Premium）** | $1.05                | $1,999         | 提供高级功能及优先支持服务。                           |  
| **企业版（Enterprise）**| 自定义报价           | 联系我们        | 可定制的顶级企业解决方案。                           |  

🚀 **特别优惠**：首次充值达最高 **$500**，我们将同额返还！

## **开发者喜爱 LinkedIn 验证码解决方案的原因**  
- **集成方便**：与 Puppeteer、Playwright、Selenium 等工具无缝对接。  
- **AI 智能逻辑**：自动处理重试、验证码解决、指纹、IP 轮换和复杂请求头。  
- **内置浏览器**：无需额外管理第三方浏览器即可完成 JavaScript 渲染。  
- **实时洞察**：通过实时仪表盘监控网络性能。  
- **卓越支持**：全球 24/7 客户服务，并持续快速迭代新功能。

## **常见问题 (FAQ)**

### **LinkedIn 验证码解决方案如何运作？**  
该方案利用先进的 AI 逻辑自动检测并解决 LinkedIn 验证码，无需人工干预。

### **能否同时处理多个验证码？**  
可以。系统可同时处理多种验证码类型，确保连续无阻的访问速度。

### **如果验证码破解失败怎么办？**  
系统会自动重试。如仍遇到问题，可联系我们 24/7 全天候支持团队进行排查。

---

## **告别 LinkedIn 验证码的束缚**  
立即开始免费试用，体验 [Bright Data 的 LinkedIn 验证码解决方案](https://www.bright.cn/products/web-unlocker/captcha-solver/linkedIn)，轻松畅享无障碍访问！
