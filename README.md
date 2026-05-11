import React, { useMemo, useState } from 'react';
import { 
  Eye, Palette, FileText, Layers, ChevronDown, 
  Wand2, FileDown, Copy, Code, Loader2, Sparkles, Upload,
  LayoutTemplate, Type, Heading, Puzzle, PaintBucket, Image as ImageIcon, CheckSquare
} from 'lucide-react';

// --- 字体库 ---
const fontOptions = {
  hei: '"Noto Sans SC", "Microsoft YaHei", sans-serif',
  song: '"Noto Serif SC", "SimSun", serif',
  kai: '"KaiTi", "STKaiti", serif',
  fangsong: '"FangSong", "STFangsong", serif',
  english: '"Comic Sans MS", "Times New Roman", Arial, sans-serif', 
  handwritten: '"Ma Shan Zheng", "Zhi Mang Xing", "KaiTi", cursive', 
};

const templatePresets = {
  morningDictation: { 
    paperWidth: 1080, paperHeight: 1440, globalColumns: 3, paddingV: 50, paddingH: 50,
    paperBorder: 'none', paperBorderColor: '#166534',
    baseFont: fontOptions.song, baseSize: 20, lineHeight: 1.6, paragraphSpacing: 22, baseColor: '#111827',
    metaFont: fontOptions.song, metaSize: 16,
    h1Font: fontOptions.hei, h1Size: 34, h1Color: '#166534', h1Deco: 'none', h1Align: 'center', h1Bold: true,
    h2Font: fontOptions.english, h2Size: 28, h2Color: '#166534', h2Deco: 'none', h2Align: 'center', h2Bold: true,
    h3Font: fontOptions.hei, h3Size: 24, h3Color: '#166534', h3Deco: 'none', h3Align: 'left', h3Bold: true,
    focusFont: fontOptions.english, focusSize: 28, focusColor: '#dc2626', focusDeco: 'none', 
    paperBg: '#ffffff', boxBg: '#f8fafc', zoom: 55,
    showPageNumber: true, showBrand: true, brandTag: '核心默写单', itemsPerPage: 45
  },
  coreDictation: { 
    paperWidth: 1080, paperHeight: 1440, globalColumns: 3, paddingV: 40, paddingH: 40,
    paperBorder: 'none', paperBorderColor: '#2563eb',
    baseFont: fontOptions.hei, baseSize: 20, lineHeight: 1.6, paragraphSpacing: 24, baseColor: '#334155',
    metaFont: fontOptions.song, metaSize: 16,
    h1Font: fontOptions.hei, h1Size: 32, h1Color: '#2563eb', h1Deco: 'capsule', h1Align: 'center', h1Bold: true,
    h2Font: fontOptions.english, h2Size: 26, h2Color: '#2563eb', h2Deco: 'capsule', h2Align: 'center', h2Bold: true,
    h3Font: fontOptions.hei, h3Size: 22, h3Color: '#2563eb', h3Deco: 'none', h3Align: 'left', h3Bold: true,
    focusFont: fontOptions.english, focusSize: 28, focusColor: '#dc2626', focusDeco: 'none', 
    paperBg: '#ffffff', boxBg: '#f8fafc', zoom: 55,
    showPageNumber: true, showBrand: true, brandTag: '核心讲义', itemsPerPage: 45
  }
};

const initialContent = `# 2026春湘少版小升初英语单词复习清单（六年级全册）·师生共用版

> 💡 默写/翻译本｜四会词要求会拼写｜三会词只要求听说认读｜词组、句型按中译英操练。

---

# 六年级上册

## Unit 1  What did you do during the holidays?
信息栏[班级(Class): ________  姓名(Name): ________  得分(Score): ________]
侧边栏[订正栏]

### 一、四会词（听说读写）
1. /ˈdjʊərɪŋ/ prep. 在……期间
   英[during]
2. /ˈhɒlədeɪ/ n. 假日；假期
   英[holiday]
3. /lɜːn/ v. 学习
   英[learn]
4. /ˈpræktɪs/ v. 练习
   英[practise]
5. /spiːk/ v. 说
   英[speak]
6. /riːd/ v. 读
   英[read]
7. /raɪt/ v. 写
   英[write]
8. /pleɪ/ v. 玩
   英[play]
9. /ɡəʊ/ v. 去
   英[go]
10. /hæv/ v. 有；进行
    英[have]

### 二、三会词（听说读）
1. /bel/ n. 铃
   英[bell]
2. /rɪŋ/ v. 鸣；响
   英[ring]
3. /waɪ/ adv. 为什么
   英[why]

### 三、重点词组（中译英）
1. 在假期期间   [during the holidays]
2. 学习单词和句子 [learn words and sentences]
3. 学习写作 [learn writing]
4. 练习听力  [practise listening]
5. 玩游戏   [play games]
6. 看望祖父母 [visit grandparents]
7. 读很多书 [read many books]
8. 谈论   [talk about]
9. 拿出   [take out]
10. 走出  [go out of]

### 四、重点句型（中译英）
1. 你假期里做了什么？   [What did you do during the holidays?]
2. 我假期里读了很多书。 [I read many books during the holidays.]
3. 我学习了写作。 [I learnt writing.]
4. 安妮假期里用英语写了一本故事书。  [Anne wrote a storybook in English during the holidays.]
5. 你为什么不绕着树跑？ [Why didn't you run around the tree?]
6. 下课了！  [Class is over!]

---

## Unit 2  Katie always gets up early
信息栏[班级(Class): ________  姓名(Name): ________  得分(Score): ________]
侧边栏[订正栏]

### 一、四会词（听说读写）
1. /ˈɔːlweɪz/ adv. 总是；经常
   英[always]
2. /ˈwiːkdeɪ/ n. 平日
   英[weekday]
3. /ˈɒfn/ adv. 常常；时常
   英[often]
4. /ˈɑːftə(r)/ prep. 在……之后
   英[after]
5. /weɪv/ v. 挥手
   英[wave]
6. /rɪˈtɜːn/ v. 返回
   英[return]
7. /ˈsʌmtaɪmz/ adv. 有时
   英[sometimes]
8. /ˈnevə(r)/ adv. 从不
   英[never]

### 二、三会词（听说读）
1. /ˈɜːli/ adv. 早；提早
   英[early]
2. /hɜːt/ v. 伤害
   英[hurt]
3. /əbˈzɜːv/ v. 观察
   英[observe]
4. /ˈsaɪəntɪst/ n. 科学家
   英[scientist]
5. /weɪt/ v. 等；等待
   英[wait]

### 三、重点词组（中译英）
1. 早起   [get up early]
2. 在平日   [on weekdays]
3. 吃早餐   [have breakfast]
4. 挥手告别   [wave goodbye]
5. 去上学   [go to school]
6. 回家   [return home]
7. 做家庭作业   [do homework]
8. 下棋   [play chess]
9. 散步   [take a walk]
10. 上学迟到   [be late for school]

### 四、重点句型（中译英）
1. 凯蒂总是起得很早。   [Katie always gets up early.]
2. 平日，她总是早上 6:30 起床。   [On weekdays, she always gets up at 6:30 a.m.]
3. 她的家人经常早上 6:45 吃早餐。   [Her family often has breakfast at 6:45 a.m.]
4. 她经常晚饭前做家庭作业。   [She often does her homework before dinner.]
5. 他将要观察它们。   [He is going to observe them.]

---

## Unit 3  I like my computer
信息栏[班级(Class): ________  姓名(Name): ________  得分(Score): ________]
侧边栏[订正栏]

### 一、四会词（听说读写）
1. /sɜːtʃ/ v. 查找；寻找
   英[search]
2. /wɜːld/ n. 世界
   英[world]
3. /ˈiːmeɪl/ n.&v. 电子邮件；发邮件
   英[email]
4. /send/ v. 发送；寄
   英[send]
5. /ˈɡriːtɪŋ/ n. 问候
   英[greeting]
6. /kəmˈpjuːtə(r)/ n. 电脑
   英[computer]
7. /faɪnd/ v. 发现
   英[find]
8. /lɜːn/ v. 学习
   英[learn]

### 二、三会词（听说读）
1. /ˈpreznt/ n. 礼物
   英[present]
2. /ˈwʌndəfl/ adj. 极好的；精彩的
   英[wonderful]

### 三、重点词组（中译英）
1. 查找许多东西   [search for a lot of things]
2. 弄清关于国家的情况   [find out about countries]
3. 给朋友发邮件   [email my friends]
4. 发送问候   [send greetings]
5. 在电脑上做作业   [do homework on the computer]
6. 玩电脑游戏   [play computer games]
7. 一份生日礼物   [a birthday present]

### 四、重点句型（中译英）
1. 我喜欢我的电脑，它很快。   [I like my computer. It's fast.]
2. 现在我能查阅很多关于它的事情。   [Now I can search for a lot of things about it.]
3. 你也能查找世界上国家的情况。   [You can also find out about countries in the world.]
4. 它对你的眼睛不好。   [It's not good for your eyes.]
5. 他教他如何在电脑上查找很多东西。   [He teaches him how to search for many things on the computer.]
`;

// --- 核心渲染引擎 ---

function applyInlineRules(text, examMode) {
  let result = text;
  result = result.replace(/\*\*(.*?)\*\*/g, '<strong>$1</strong>');
  result = result.replace(/拼\[(.*?)\]\((.*?)\)/g, '<ruby class="edu-ruby">$1<rt>$2</rt></ruby>');
  result = result.replace(/批\[(.*?)\]/g, '<span class="edu-annotation">$1</span>');
  
  result = result.replace(/\[([^\]]+)\]/g, (match, p1) => {
    if (examMode === 'student') {
      return `<span class="hl-focus blank-mode">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span>`;
    } else {
      return `<span class="hl-focus teacher-mode">${p1}</span>`;
    }
  });
  
  return result;
}

function paginateMarkdown(markdown, settings) {
  const lines = markdown.split('\n');
  const pages = [];
  let currentPageLines = [];
  let currentItemCount = 0;
  
  let activeH1 = '';
  let activeMeta = '';
  let activeSidebar = '';
  
  const itemsPerPage = settings.itemsPerPage || 45;

  const flushPage = () => {
    if (currentPageLines.filter(l => l.trim() && l.trim() !== '---').length === 0) return;
    
    const hasH1 = currentPageLines.some(l => l.trim().startsWith('# '));
    const hasMeta = currentPageLines.some(l => l.trim().startsWith('信息栏'));
    const hasSidebar = currentPageLines.some(l => l.trim().startsWith('侧边栏'));

    const injectLines = [];
    if (!hasH1 && activeH1) injectLines.push(activeH1);
    if (!hasSidebar && activeSidebar) injectLines.push(activeSidebar);
    if (!hasMeta && activeMeta) injectLines.push(activeMeta);

    pages.push([...injectLines, ...currentPageLines].join('\n'));
    currentPageLines = [];
    currentItemCount = 0;
  };

  for (let i = 0; i < lines.length; i++) {
      const line = lines[i];
      const trimmed = line.trim();
      
      if (trimmed.startsWith('# ')) activeH1 = line;
      if (trimmed.startsWith('信息栏')) activeMeta = line;
      if (trimmed.startsWith('侧边栏')) activeSidebar = line;

      if (trimmed === '<div style="page-break-after: always;"></div>' || trimmed === '====') {
          flushPage();
          continue;
      }

      if (trimmed.startsWith('## ')) {
          if (currentItemCount > 0) {
              flushPage();
          }
      }

      let isContentBlock = false;
      if (trimmed && !trimmed.startsWith('#') && !trimmed.startsWith('信息栏') && !trimmed.startsWith('侧边栏') && !trimmed.startsWith('>') && trimmed !== '---') {
          isContentBlock = true;
      }

      if (/^\d+\./.test(trimmed) || trimmed.startsWith('- ') || trimmed.startsWith('英[') || trimmed.startsWith('田[')) {
          currentItemCount += 1;
      } else if (isContentBlock && currentItemCount > 0) {
          currentItemCount += 0.5; 
      }

      if (currentItemCount >= itemsPerPage) {
          flushPage();
      }

      currentPageLines.push(line);
  }

  flushPage();

  return pages;
}

function renderSinglePage(input, examMode) {
  const lines = input.split('\n');
  const headerHtml = [];
  const bodyHtml = [];
  let inHeaderPhase = true;
  let inParagraph = false;
  let hasSidebar = false;
  let sidebarTitle = '';

  const closeParagraph = () => {
    if (inParagraph) {
      bodyHtml.push('</p>');
      inParagraph = false;
    }
  };

  const pushToCorrectPhase = (htmlString) => {
    if (inHeaderPhase) headerHtml.push(htmlString);
    else bodyHtml.push(htmlString);
  };

  for (let i = 0; i < lines.length; i++) {
    const rawLine = lines[i];
    const trimmed = rawLine.trim();

    if (!trimmed) {
      closeParagraph();
      continue;
    }

    if (trimmed.startsWith('<')) {
      closeParagraph();
      pushToCorrectPhase(trimmed);
      continue;
    }

    const nextLine = i + 1 < lines.length ? lines[i+1].trim() : '';
    const isHeaderElement = /^(#|##|###|>|信息栏|Date:)/.test(trimmed);

    if (trimmed && !isHeaderElement && !trimmed.startsWith('侧边栏') && !trimmed.startsWith('留白') && nextLine.startsWith('英[')) {
      inHeaderPhase = false;
      closeParagraph();
      const wordMatch = nextLine.match(/英\[(.*?)\]/);
      const word = wordMatch ? wordMatch[1] : '';
      const showWord = examMode === 'teacher';
      const wordHtml = `<div class="eng-grid"><div class="eng-lines"></div><span class="eng-text ${showWord ? 'show-answer' : 'hide-answer'}">${word}</span></div>`;
      bodyHtml.push(`<div class="dictation-block edu-break-avoid"><div class="dictation-text">${applyInlineRules(trimmed, examMode)}</div>${wordHtml}</div>`);
      i++; 
      continue;
    }

    if (trimmed && !isHeaderElement && !trimmed.startsWith('侧边栏') && !trimmed.startsWith('留白') && nextLine.startsWith('田[')) {
      inHeaderPhase = false;
      closeParagraph();
      const wordHtml = nextLine.replace(/田\[(.*?)\]\((.*?)\)/g, (match, char, pinyin) => {
        const showChar = examMode === 'teacher';
        return `<div class="tianzi-container"><div class="pinyin">${pinyin}</div><div class="tianzi-box"><span class="char ${showChar ? 'show-answer' : 'hide-answer'}">${char}</span></div></div>`;
      });
      bodyHtml.push(`<div class="dictation-block edu-break-avoid"><div class="dictation-text">${applyInlineRules(trimmed, examMode)}</div><div class="components-row">${wordHtml}</div></div>`);
      i++; 
      continue;
    }

    if (trimmed.startsWith('侧边栏[')) {
      closeParagraph();
      hasSidebar = true;
      const match = trimmed.match(/侧边栏\[(.*?)\]/);
      sidebarTitle = match ? match[1] : '订正栏';
      continue;
    }

    if (trimmed.startsWith('Date:') || trimmed.startsWith('信息栏[')) {
      closeParagraph();
      let parts = [];
      if (trimmed.startsWith('Date:')) {
         parts = trimmed.split(/\s{2,}|\t/).filter(Boolean);
      } else {
         const metaMatch = trimmed.match(/信息栏\[(.*?)\]/);
         if (metaMatch) parts = metaMatch[1].split(/\s{2,}|\t/).filter(Boolean);
      }
      const spans = parts.map(p => `<span>${p}</span>`).join('');
      pushToCorrectPhase(`<div class="edu-meta">${spans}</div>`);
      continue;
    }

    if (trimmed.startsWith('### ')) {
      closeParagraph();
      pushToCorrectPhase(`<h3>${applyInlineRules(trimmed.slice(4), examMode)}</h3>`);
      continue;
    }

    if (trimmed.startsWith('## ')) {
      closeParagraph();
      pushToCorrectPhase(`<h2>${applyInlineRules(trimmed.slice(3), examMode)}</h2>`);
      continue;
    }

    if (trimmed.startsWith('# ')) {
      closeParagraph();
      pushToCorrectPhase(`<h1>${applyInlineRules(trimmed.slice(2), examMode)}</h1>`);
      continue;
    }

    if (trimmed.startsWith('> ')) {
      closeParagraph();
      pushToCorrectPhase(`<blockquote class="edu-quote edu-break-avoid">${applyInlineRules(trimmed.slice(2), examMode)}</blockquote>`);
      continue;
    }

    if (trimmed === '---') {
      closeParagraph();
      pushToCorrectPhase('<hr class="edu-hr" />');
      continue;
    }

    const blankMatch = trimmed.match(/留白\[(\d+)\]/);
    if (blankMatch) {
      inHeaderPhase = false;
      closeParagraph();
      bodyHtml.push(`<div class="edu-blank-box edu-break-avoid" style="height: ${blankMatch[1]}px;">(预留作答区 ${blankMatch[1]}px)</div>`);
      continue;
    }

    inHeaderPhase = false; 
    if (!inParagraph) {
      bodyHtml.push('<p>');
      inParagraph = true;
    } else {
      bodyHtml.push('<br/>');
    }
    bodyHtml.push(applyInlineRules(trimmed, examMode));
  }

  closeParagraph();

  let finalHtml = '';
  if (headerHtml.length > 0) {
    finalHtml += `<div class="page-header">${headerHtml.join('')}</div>`;
  }

  if (hasSidebar) {
    finalHtml += `
      <div class="page-body has-sidebar">
        <div class="dictation-cols">${bodyHtml.join('')}</div>
        <div class="correction-col"><div class="correction-box">${sidebarTitle}</div></div>
      </div>`;
  } else {
    finalHtml += `<div class="page-body no-sidebar"><div class="dictation-cols">${bodyHtml.join('')}</div></div>`;
  }

  return { html: finalHtml, hasSidebar };
}

function renderMixedContent(input, settings, examMode) {
  const pagesText = paginateMarkdown(input, settings);
  let hasGlobalSidebar = false;
  
  const html = pagesText.map((pageText, index) => {
    if (!pageText.trim()) return '';
    const { html: pageHtml, hasSidebar } = renderSinglePage(pageText, examMode);
    if (hasSidebar) hasGlobalSidebar = true;
    const separator = index < pagesText.length - 1 ? `<div class="page-break-indicator"></div>` : '';
    
    const footerHtml = `
      <div class="edu-footer">
        ${settings.showBrand ? `
        <div class="brand-watermark">
          <div class="brand-text">
            <span class="angie-name">Angie</span>
            ${settings.brandTag ? `<span class="brand-tag">${settings.brandTag}</span>` : ''}
          </div>
        </div>
        ` : '<div></div>'}
        ${settings.showPageNumber ? `<div class="page-num"> - ${index + 1} - </div>` : '<div></div>'}
      </div>
    `;

    return `<div class="page-wrapper">${pageHtml}${footerHtml}</div>${separator}`;
  }).join('');

  return { html, hasSidebar: hasGlobalSidebar };
}

function buildPreviewCss(settings) {
  let h1Bg = 'transparent', h1TextColor = settings.h1Color, h1Padding = '0', h1Radius = '0', h1Border = 'none';
  if (settings.h1Deco === 'capsule' || settings.h1Deco === 'fill-box') { 
    h1Bg = settings.h1Color; h1TextColor = '#fff'; h1Padding = '8px 36px'; h1Radius = '99px'; 
  } else if (settings.h1Deco === 'rounded-box') {
    h1Bg = settings.h1Color; h1TextColor = '#fff'; h1Padding = '8px 24px'; h1Radius = '8px'; 
  } else if (settings.h1Deco === 'dashed-box') {
    h1Border = `3px dashed ${settings.h1Color}`; h1Padding = '8px 24px'; h1Radius = '8px'; 
  } else if (settings.h1Deco === 'outline-box') {
    h1Border = `3px solid ${settings.h1Color}`; h1Padding = '8px 24px'; h1Radius = '8px'; 
  }
  const isH1Box = ['capsule', 'fill-box', 'rounded-box', 'dashed-box', 'outline-box'].includes(settings.h1Deco);

  let h2Bg = 'transparent', h2Color = settings.h2Color, h2Border = 'none', h2Radius = '0', h2Padding = '0', h2Deco = 'none';
  if (settings.h2Deco === 'capsule' || settings.h2Deco === 'fill-box') { 
    h2Bg = settings.h2Color; h2Color = '#fff'; h2Padding = '4px 28px'; h2Radius = '99px'; 
  } else if (settings.h2Deco === 'rounded-box') { 
    h2Bg = settings.h2Color; h2Color = '#fff'; h2Padding = '4px 18px'; h2Radius = '6px'; 
  } else if (settings.h2Deco === 'outline-box') { 
    h2Border = `2px solid ${settings.h2Color}`; h2Padding = '6px 14px'; h2Radius = '6px'; 
  } else if (settings.h2Deco === 'dashed-box') { 
    h2Border = `2px dashed ${settings.h2Color}`; h2Padding = '6px 14px'; h2Radius = '6px'; 
  } else if (settings.h2Deco === 'left-bar') { 
    h2Border = 'none'; h2Padding = '2px 12px'; 
  } else if (settings.h2Deco === 'underline') { 
    h2Deco = 'underline'; h2Padding = '2px 0'; 
  }
  const isH2Box = ['capsule', 'fill-box', 'rounded-box', 'dashed-box', 'outline-box'].includes(settings.h2Deco);

  let h3Bg = 'transparent', h3Color = settings.h3Color, h3Border = 'none', h3Radius = '0', h3Padding = '0', h3Deco = 'none';
  if (settings.h3Deco === 'capsule' || settings.h3Deco === 'fill-box') { 
    h3Bg = settings.h3Color; h3Color = '#fff'; h3Padding = '4px 18px'; h3Radius = '99px'; 
  } else if (settings.h3Deco === 'rounded-box') { 
    h3Bg = settings.h3Color; h3Color = '#fff'; h3Padding = '4px 12px'; h3Radius = '4px'; 
  } else if (settings.h3Deco === 'outline-box') { 
    h3Border = `1.5px solid ${settings.h3Color}`; h3Padding = '4px 12px'; h3Radius = '4px'; 
  } else if (settings.h3Deco === 'dashed-box') { 
    h3Border = `1.5px dashed ${settings.h3Color}`; h3Padding = '4px 12px'; h3Radius = '4px'; 
  } else if (settings.h3Deco === 'left-bar') { 
    h3Border = 'none'; h3Padding = '1px 10px'; 
  } else if (settings.h3Deco === 'underline') { 
    h3Deco = 'underline'; h3Padding = '1px 0'; 
  }
  const isH3Box = ['capsule', 'fill-box', 'rounded-box', 'dashed-box', 'outline-box'].includes(settings.h3Deco);

  let borderCss = '';
  if (settings.paperBorder === 'solid') borderCss = `border: 2px solid ${settings.paperBorderColor};`;
  else if (settings.paperBorder === 'dashed') borderCss = `border: 2px dashed ${settings.paperBorderColor};`;
  else if (settings.paperBorder === 'double') borderCss = `border: 4px double ${settings.paperBorderColor};`;
  else if (settings.paperBorder === 'double-dashed') borderCss = `border: 4px dashed ${settings.paperBorderColor}; border-radius: 16px;`;

  return `
    .paper-root {
      background: transparent;
      margin: 0 auto;
      color: ${settings.baseColor};
      font-family: ${settings.baseFont};
      font-size: ${settings.baseSize}px;
      font-weight: ${settings.baseBold ? 'bold' : 'normal'};
      line-height: ${settings.lineHeight};
      letter-spacing: ${settings.letterSpacing || 0}px;
    }
    
    .paper-root * { box-sizing: border-box; }
    .paper-root strong { font-weight: bold; }
    
    .paper-root .page-wrapper {
      position: relative;
      width: ${settings.paperWidth}px;
      /* 修复点1：严格固定高度，替换原本会导致高度随内容拉伸的 min-height */
      height: ${settings.paperHeight}px; 
      max-height: ${settings.paperHeight}px;
      overflow: hidden; /* 防止溢出内容撑破固定尺寸 */
      padding: ${settings.paddingV}px ${settings.paddingH}px;
      padding-bottom: ${settings.paddingV + 60}px;
      background: ${settings.paperBg};
      margin: 0 auto 30px auto;
      box-shadow: 0 10px 25px rgba(0,0,0,0.1);
      ${borderCss}
    }

    ${settings.paperBorder === 'double-dashed' ? `
    .paper-root .page-wrapper::after {
      content: '';
      position: absolute;
      top: 10px; left: 10px; right: 10px; bottom: 10px;
      border: 2px dashed ${settings.paperBorderColor};
      border-radius: 10px;
      pointer-events: none;
    }
    ` : ''}

    .paper-root .page-header { margin-bottom: 25px; }
    
    .paper-root .page-body.has-sidebar {
      display: grid;
      /* 外层网格永远保持 3:1 */
      grid-template-columns: 3fr 1fr;
      gap: 30px;
      align-items: stretch;
    }

    .paper-root .page-body.no-sidebar .dictation-cols {
      column-count: ${settings.globalColumns};
      column-gap: 30px;
    }
    
    .paper-root .page-body.has-sidebar .dictation-cols {
      /* 内容区内部分栏 */
      column-count: ${settings.globalColumns};
      column-gap: 30px;
      min-width: 0;
    }

    .paper-root .correction-col {
      display: flex;
      flex-direction: column;
      min-width: 0;
    }

    .paper-root .correction-box {
      flex: 1; 
      border: 1.5px solid ${settings.paperBorderColor};
      padding: 16px;
      text-align: center;
      color: ${settings.baseColor};
      font-size: ${settings.metaSize || 16}px;
      font-family: ${settings.metaFont || 'inherit'};
      border-radius: 2px;
    }
    
    .paper-root h1, .paper-root h2, .paper-root h3, .paper-root .edu-meta { 
      column-span: all; 
      break-after: avoid; 
      page-break-after: avoid;
    }

    .paper-root h1 {
      text-align: ${settings.h1Align || 'center'};
      font-family: ${settings.h1Font};
      font-size: ${settings.h1Size}px;
      color: ${h1TextColor};
      background: ${h1Bg};
      padding: ${h1Padding};
      border-radius: ${h1Radius};
      border: ${h1Border};
      font-weight: ${settings.h1Bold !== false ? '800' : 'normal'};
      margin: 0 ${settings.h1Align === 'center' ? 'auto' : '0'} 20px ${settings.h1Align === 'center' ? 'auto' : '0'};
      text-decoration: ${settings.h1Deco === 'underline' ? 'underline' : 'none'};
      text-underline-offset: 8px;
      display: block;
      width: ${isH1Box ? 'fit-content' : '100%'};
    }
    
    .paper-root h2 {
      text-align: ${settings.h2Align || 'center'};
      font-family: ${settings.h2Font};
      font-size: ${settings.h2Size}px;
      color: ${h2Color};
      background: ${h2Bg};
      border: ${h2Border};
      border-left: ${settings.h2Deco === 'left-bar' ? `6px solid ${settings.h2Color}` : (h2Border !== 'none' ? h2Border : 'none')};
      padding: ${h2Padding};
      border-radius: ${h2Radius};
      text-decoration: ${h2Deco};
      text-underline-offset: 4px;
      font-weight: ${settings.h2Bold !== false ? '700' : 'normal'};
      margin: 15px ${settings.h2Align === 'center' ? 'auto' : '0'} 25px ${settings.h2Align === 'center' ? 'auto' : '0'};
      display: block;
      width: ${isH2Box ? 'fit-content' : '100%'};
    }
    
    .paper-root h3 {
      text-align: ${settings.h3Align || 'left'};
      font-family: ${settings.h3Font};
      font-size: ${settings.h3Size}px;
      color: ${h3Color};
      background: ${h3Bg};
      border: ${h3Border};
      border-left: ${settings.h3Deco === 'left-bar' ? `4px solid ${settings.h3Color}` : (h3Border !== 'none' ? h3Border : 'none')};
      padding: ${h3Padding};
      border-radius: ${h3Radius};
      text-decoration: ${h3Deco};
      text-underline-offset: 4px;
      font-weight: ${settings.h3Bold !== false ? '700' : 'normal'};
      margin: 15px ${settings.h3Align === 'center' ? 'auto' : '0'} 12px ${settings.h3Align === 'center' ? 'auto' : '0'};
      display: block;
      width: ${isH3Box ? 'fit-content' : '100%'};
    }
    
    .paper-root p { margin: 0 0 ${settings.paragraphSpacing}px 0; }
    
    .paper-root .edu-meta {
      display: flex;
      justify-content: space-between;
      margin-bottom: 25px;
      font-family: ${settings.metaFont || 'inherit'};
      font-size: ${settings.metaSize || 16}px;
      color: ${settings.baseColor};
    }

    .paper-root .hl-focus.blank-mode {
      display: inline-block;
      min-width: 40px;
      border-bottom: 1.5px solid ${settings.baseColor};
      text-decoration: none;
      font-family: ${settings.focusFont};
      font-size: ${settings.focusSize}px;
    }
    .paper-root .hl-focus.teacher-mode {
      color: ${settings.focusColor};
      border-bottom: 1.5px solid ${settings.baseColor};
      padding: 0 4px;
      font-weight: ${settings.focusBold !== false ? 'bold' : 'normal'};
      font-family: ${settings.focusFont};
      font-size: ${settings.focusSize}px;
    }

    .paper-root .dictation-block {
      display: inline-block;
      break-inside: avoid;
      page-break-inside: avoid;
      -webkit-column-break-inside: avoid; 
      margin-bottom: ${settings.paragraphSpacing}px;
      width: 100%;
    }
    
    .paper-root .dictation-text {
      font-size: ${settings.baseSize}px;
      font-family: ${settings.baseFont};
      font-weight: ${settings.baseBold ? 'bold' : 'normal'};
      color: ${settings.baseColor};
      margin-bottom: 2px;
    }

    .paper-root .eng-grid { 
      display: block; 
      position: relative; 
      width: 100%; 
      height: 38px; 
      margin-top: 4px; 
    }
    .paper-root .eng-lines {
      position: absolute; 
      top: 10px; 
      left: 0; 
      right: 0; 
      height: 28px;
      background: linear-gradient(
        to bottom,
        #94a3b8 1px, transparent 1px, 
        transparent 9px, #fca5a5 10px, transparent 10px, 
        transparent 18px, #fca5a5 19px, transparent 19px, 
        transparent 27px, #94a3b8 28px 
      );
    }
    .paper-root .eng-text { 
      position: absolute; 
      left: 10px; 
      bottom: 9px; 
      font-family: ${settings.focusFont}; 
      font-size: ${settings.focusSize}px; 
      font-weight: ${settings.focusBold !== false ? 'bold' : 'normal'};
      line-height: 1; 
      letter-spacing: 1px;
    }
    .paper-root .eng-text.hide-answer { opacity: 0; }
    .paper-root .eng-text.show-answer { opacity: 1; color: ${settings.focusColor}; }

    .paper-root .tianzi-container { display: inline-flex; flex-direction: column; align-items: center; margin-right: 12px; }
    .paper-root .tianzi-container .pinyin { font-size: 14px; color: #64748b; height: 20px; font-family: ${fontOptions.english}; }
    .paper-root .tianzi-box {
      width: 56px; height: 56px;
      border: 2px solid ${settings.focusColor};
      position: relative; display: flex; align-items: center; justify-content: center;
      background-image: 
        linear-gradient(to bottom, transparent 49%, ${settings.focusColor} 49%, ${settings.focusColor} 51%, transparent 51%),
        linear-gradient(to right, transparent 49%, ${settings.focusColor} 49%, ${settings.focusColor} 51%, transparent 51%),
        linear-gradient(45deg, transparent 49.5%, ${settings.focusColor} 49.5%, ${settings.focusColor} 50.5%, transparent 50.5%),
        linear-gradient(-45deg, transparent 49.5%, ${settings.focusColor} 49.5%, ${settings.focusColor} 50.5%, transparent 50.5%);
      opacity: 0.8;
    }
    .paper-root .tianzi-box .char { font-size: 38px; font-family: ${fontOptions.kai}; font-weight: ${settings.focusBold !== false ? 'bold' : 'normal'}; z-index: 1; }
    .paper-root .tianzi-box .char.hide-answer { opacity: 0; }
    .paper-root .tianzi-box .char.show-answer { opacity: 1; color: ${settings.focusColor}; }

    .paper-root .edu-quote { background: ${settings.boxBg}; border-left: 4px solid ${settings.h2Color}; padding: 12px 16px; margin: 15px 0; font-family: ${fontOptions.kai}; }
    .paper-root .edu-annotation { float: right; background-color: #fef2f2; color: #ef4444; border: 1px solid #fca5a5; padding: 2px 8px; border-radius: 12px; font-size: 13px; font-family: ${fontOptions.kai}; margin-left: 15px; margin-bottom: 5px; }
    .paper-root .edu-hr { border: none; border-top: 2px dashed #cbd5e1; margin: 25px 0; }

    .edu-footer {
      position: absolute;
      bottom: ${settings.paddingV / 1.5}px;
      left: ${settings.paddingH}px;
      right: ${settings.paddingH}px;
      display: flex;
      justify-content: space-between;
      align-items: flex-end;
    }
    .brand-watermark {
      display: flex;
      align-items: center;
      gap: 6px;
    }
    .brand-text {
      display: flex;
      align-items: baseline;
    }
    .angie-name {
      font-family: ${fontOptions.handwritten};
      font-size: 26px;
      font-weight: 800;
      color: ${settings.h1Color};
      font-style: italic;
    }
    .brand-tag {
      background: ${settings.h1Color};
      color: #fff;
      font-size: 13px;
      padding: 3px 8px;
      border-radius: 6px;
      margin-left: 8px;
      margin-bottom: 4px;
    }
    .page-num {
      font-family: ${fontOptions.english};
      font-size: 16px;
      font-weight: bold;
      color: #64748b;
    }

    .page-break-indicator { 
      page-break-after: always;
      break-after: page;
      margin: 40px -${settings.paddingH}px;
      border-top: 2px dashed #94a3b8;
      text-align: center;
      position: relative;
    }
    .page-break-indicator::after {
      content: '✂ 断页线 / Page Break';
      position: absolute;
      top: -12px;
      left: 50%;
      transform: translateX(-50%);
      background: ${settings.paperBg};
      padding: 0 10px;
      color: #94a3b8;
      font-size: 12px;
    }
    
    @media print {
      @page { size: ${settings.paperWidth}px ${settings.paperHeight}px; margin: 0; }
      body { margin: 0; -webkit-print-color-adjust: exact; print-color-adjust: exact; background: transparent; }
      .paper-root .page-wrapper { margin-bottom: 0; box-shadow: none; }
      .page-break-indicator { display: none; }
    }
  `;
}

const Accordion = ({ title, icon, defaultOpen = false, children }) => {
  const [isOpen, setIsOpen] = useState(defaultOpen);
  return (
    <div className="border border-slate-200 rounded-lg bg-white mb-3 shadow-sm overflow-hidden transition-all duration-200">
      <button onClick={() => setIsOpen(!isOpen)} className="w-full px-3 py-3 flex justify-between items-center bg-slate-50 hover:bg-slate-100 transition-colors">
        <span className="font-semibold text-sm text-slate-800 flex items-center gap-2">
          {icon} {title}
        </span>
        <ChevronDown className={`w-4 h-4 text-slate-500 transition-transform duration-200 ${isOpen ? 'rotate-180' : ''}`} />
      </button>
      <div className={`transition-all duration-300 ease-in-out ${isOpen ? 'max-h-[2000px] opacity-100' : 'max-h-0 opacity-0'}`} style={{ overflow: isOpen ? 'visible' : 'hidden' }}>
        <div className="p-3 border-t border-slate-100 bg-white">
          {children}
        </div>
      </div>
    </div>
  );
};

const NumberInput = ({ label, value, onChange, min, max, step=1 }) => (
  <div className="flex flex-col gap-1.5">
    <label className="text-[11px] font-medium text-slate-600">{label}</label>
    <input type="number" min={min} max={max} step={step} value={value} onChange={e => { if (e?.target) onChange(Number(e.target.value)); }} className="w-full rounded-md border border-slate-300 px-2 py-1.5 text-[13px] focus:border-blue-500 outline-none" />
  </div>
);

const SelectInput = ({ label, value, onChange, options }) => (
  <div className="flex flex-col gap-1.5">
    <label className="text-[11px] font-medium text-slate-600">{label}</label>
    <select value={value} onChange={e => { if (e?.target) onChange(e.target.value); }} className="w-full rounded-md border border-slate-300 px-2 py-1.5 text-[13px] focus:border-blue-500 outline-none">
      {options?.map(opt => <option key={opt.value} value={opt.value}>{opt.label}</option>)}
    </select>
  </div>
);

const ColorPicker = ({ label, value, onChange }) => (
  <div className="flex flex-col gap-1.5 items-start">
    <label className="text-[11px] font-medium text-slate-600">{label}</label>
    <div className="flex items-center gap-2 border border-slate-200 rounded-md p-1 pr-2 bg-white w-full">
      <input type="color" value={value} onChange={e => { if (e?.target) onChange(e.target.value); }} className="w-6 h-6 rounded cursor-pointer border-none p-0 bg-transparent shrink-0" />
      <span className="text-[10px] font-mono text-slate-500 uppercase flex-1">{value}</span>
    </div>
  </div>
);

const apiKey = ""; 

async function callGemini(prompt) {
  const url = `https://generativelanguage.googleapis.com/v1beta/models/gemini-2.5-flash-preview-09-2025:generateContent?key=${apiKey}`;
  const payload = { contents: [{ parts: [{ text: prompt }] }] };

  let retries = 5;
  let delay = 1000;
  
  while (retries > 0) {
    try {
      const response = await fetch(url, { method: "POST", headers: { "Content-Type": "application/json" }, body: JSON.stringify(payload) });
      if (!response.ok) throw new Error(`HTTP error! status: ${response.status}`);
      const data = await response.json();
      return data.candidates?.[0]?.content?.parts?.[0]?.text || '';
    } catch (error) {
      retries--;
      if (retries === 0) throw error;
      await new Promise(res => setTimeout(res, delay));
      delay *= 2;
    }
  }
}

export default function App() {
  const [content, setContent] = useState(initialContent);
  const [activeTab, setActiveTab] = useState('design');
  const [presetName, setPresetName] = useState('morningDictation');
  const [settings, setSettings] = useState(templatePresets.morningDictation);
  const [jsonImport, setJsonImport] = useState('');
  
  const [isGenerating, setIsGenerating] = useState(false);
  const [isExporting, setIsExporting] = useState(false); // 新增控制截图无动画干扰的状态
  const [examMode, setExamMode] = useState('teacher'); 
  const [activeAiTask, setActiveAiTask] = useState(null);

  const { html: renderedContent } = useMemo(() => renderMixedContent(content, settings, examMode), [content, settings, examMode]);
  const previewCss = useMemo(() => buildPreviewCss(settings), [settings]);

  const set = (key, value) => setSettings(s => ({ ...s, [key]: value }));

  const fontSelectOptions = [
    {label: '黑体 (雅黑)', value: fontOptions.hei},
    {label: '宋体 (标准)', value: fontOptions.song},
    {label: '楷体 (护眼)', value: fontOptions.kai},
    {label: '仿宋 (严谨)', value: fontOptions.fangsong},
    {label: '手绘体 (活泼)', value: fontOptions.handwritten},
    {label: '英文手写 (Comic)', value: fontOptions.english}
  ];

  const commonDecoOptions = [
    {label: '无装饰', value: 'none'},
    {label: '胶囊色块', value: 'capsule'},
    {label: '圆角色块', value: 'rounded-box'},
    {label: '虚线方框', value: 'dashed-box'},
    {label: '实线方框', value: 'outline-box'},
    {label: '左侧竖条', value: 'left-bar'},
    {label: '底部下划线', value: 'underline'}
  ];

  const handleExportImage = async () => {
    setIsGenerating(true);
    setIsExporting(true); // 剥离动画影响
    const originalZoom = settings.zoom;
    set('zoom', 100); 

    setTimeout(async () => {
      try {
        if (!window.html2canvas) {
           await new Promise((resolve, reject) => {
             const script = document.createElement('script');
             script.src = 'https://cdnjs.cloudflare.com/ajax/libs/html2canvas/1.4.1/html2canvas.min.js';
             script.onload = resolve;
             script.onerror = reject;
             document.head.appendChild(script);
           });
        }
        
        const pages = document.querySelectorAll('.paper-root .page-wrapper');
        for (let i = 0; i < pages.length; i++) {
           const canvas = await window.html2canvas(pages[i], { 
               scale: 2, // 修复点2：保持二倍超清不糊，但严格锁死宽和高
               width: settings.paperWidth,
               height: settings.paperHeight,
               useCORS: true,
               backgroundColor: settings.paperBg
           });
           const link = document.createElement('a');
           link.download = `雅韵排版_第${i+1}页.png`;
           link.href = canvas.toDataURL('image/png');
           link.click();
           await new Promise(res => setTimeout(res, 500)); 
        }
      } catch (err) {
        alert('导出图片失败，请重试：' + err.message);
      } finally {
        set('zoom', originalZoom); 
        setIsGenerating(false);
        setIsExporting(false); // 恢复动画
      }
    }, 800); // 留足 800ms 确保字体、DOM完全渲染完成
  };

  const handlePrint = () => {
    const baseUri = window.location.href.replace(/\/[^/]*$/, '/');
    
    const htmlContent = `
      <!DOCTYPE html>
      <html>
      <head>
        <meta charset="utf-8">
        <base href="${baseUri}">
        <title>排版导出 - 请在对话框中选择“另存为PDF”</title>
        <style>
          ${previewCss}
          @media print {
            @page { size: A4; margin: 0; }
            body { background: #ffffff !important; margin: 0 !important; padding: 0 !important; -webkit-print-color-adjust: exact !important; print-color-adjust: exact !important; }
            .paper-root { box-shadow: none !important; margin: 0 auto !important; zoom: 73.5%; }
            .paper-root .page-wrapper { margin: 0 !important; box-shadow: none !important; page-break-after: always !important; height: ${settings.paperHeight}px !important; max-height: ${settings.paperHeight}px !important; overflow: hidden !important; }
            .page-break-indicator { display: none !important; }
          }
        </style>
      </head>
      <body>
        <div class="paper-root">
          ${renderedContent}
        </div>
        <script>
          window.onload = () => {
            setTimeout(() => { window.focus(); window.print(); }, 800);
          };
        </script>
      </body>
      </html>
    `;

    const printWindow = window.open('', '_blank');
    if (printWindow) {
      printWindow.document.open();
      printWindow.document.write(htmlContent);
      printWindow.document.close();
    } else {
      const iframe = document.createElement('iframe');
      iframe.style.position = 'absolute';
      iframe.style.width = '0px';
      iframe.style.height = '0px';
      iframe.style.border = 'none';
      document.body.appendChild(iframe);
      
      const doc = iframe.contentWindow.document;
      doc.open();
      doc.write(htmlContent);
      doc.close();
      
      setTimeout(() => { document.body.removeChild(iframe); }, 10000);
    }
  };

  const handleApplyPreset = (key) => {
    setPresetName(key);
    setSettings(templatePresets[key]);
  }

  const handleExportJson = () => setJsonImport(JSON.stringify(settings, null, 2));
  const handleImportJson = () => {
    try {
      const parsed = JSON.parse(jsonImport);
      setSettings(prev => ({...prev, ...parsed}));
      alert('母版参数汲取成功！');
    } catch(e) {
      alert('JSON 格式错误，请检查！');
    }
  };

  const handleFileUpload = (e) => {
    const file = e?.target?.files?.[0];
    if (!file) return;
    const reader = new FileReader();
    reader.onload = (event) => setContent(event?.target?.result || '');
    reader.readAsText(file);
    if (e?.target) e.target.value = null; 
  };

  const handleRandomThemeColor = () => {
    const colors = ['#0f766e', '#1d4ed8', '#b45309', '#4c1d95', '#be123c', '#15803d', '#334155'];
    const randomColor = colors[Math.floor(Math.random() * colors.length)];
    set('h1Color', randomColor);
    set('h2Color', randomColor);
    set('h3Color', randomColor);
    set('paperBorderColor', randomColor);
  };

  const insertSnippet = (snippet) => {
    setContent(c => c + '\n\n' + snippet);
  };

  const handleAiAction = async (taskType) => {
    if (isGenerating) return;
    setIsGenerating(true);
    setActiveAiTask(taskType);
    
    try {
      let prompt = "";
      if (taskType === 'smart_format') {
        prompt = `你是一个专业的英语教研员。请将以下可能是不规范的单词列表文本，重新格式化为严格的单词默写单格式。
要求：
1. 每一项必须包含序号、音标（自行推断补充）、词性、中文释义。
2. 在每个中文释义的下一行，必须严格添加 "   英[对应的英文单词]" 作为书写格子的占位符及答案，切记要把具体的英文单词放在中括号内（如 英[apple]）。
3. 如果原始文本中包含 H1 (# ) 或 H2 (## ) 的标题，请保留。
4. 请只输出格式化后的纯文本，不要包含任何 markdown 代码块符号 (如 \`\`\` 等)。

待处理文本：\n${content}`;
      } else if (taskType === 'generate_sentences') {
        prompt = `你是一个资深的 K12 英语教师。请从以下文本中识别出所有的核心英语单词，并为每个单词生成一个适合中小学生的填空题句子练习。
要求：
1. 句子要生活化，目标单词在句子中用 "[单词]" 的格式挖空。
2. 句子末尾紧跟中文翻译，格式严格为： 批[中文翻译]
3. 在句子的下一行提供正确答案，格式严格为：   英[目标单词]，切记要把具体的英文答案填在括号内。
4. 请只输出生成的练习题纯文本，不要包含任何 markdown 代码块符号 (如 \`\`\` 等)。

示例：
1. We need to save every [drop] of water. 批[我们需要节约每一滴水。]
   英[drop]

待处理文本：\n${content}`;
      } else if (taskType === 'extract_reading') {
        prompt = `你是一个英语阅读理解出题专家。请从以下阅读短文或杂乱文本中，提取出 10-15 个最核心的重点词汇（适合中小学考点）。
要求：
1. 将提取出的单词整理为默写格式：序号. /音标/ 词性. 中文释义
2. 在下一行紧跟答案格式：   英[提取的英文单词]，切记要把具体的英文单词填入括号内。
3. 请只输出格式化后的纯文本，不要输出多余的解释，不要包含 \`\`\` 符号。

待提取文本：\n${content}`;
      } else if (taskType === 'smart_fill') {
        prompt = `你是一个细心的英语教师。请严格保持下述文本的**所有原始格式、标题层级、题干和标点绝对不变**！
任务：找到文本中所有的连续下划线（如 "______" 或 "___"），将其替换为对应的正确英文答案，并用英文方括号包裹，即 "[英文答案]"。
例如：将 "1. 在假期期间   ___________" 替换为 "1. 在假期期间   [during the holidays]"。
切记：绝对不要修改我的题干和标题格式！仅做下划线到方括号答案的精准替换！只输出修改后的文本。
待处理文本：\n${content}`;
      }

      const generatedText = await callGemini(prompt);
      if (generatedText) {
        const cleanedText = generatedText.replace(/^```(markdown)?\n?/i, '').replace(/\n```$/i, '');
        setContent(cleanedText.trim());
      }
    } catch (error) {
      alert("✨ AI 处理失败，请稍后重试。原因：" + error.message);
    } finally {
      setIsGenerating(false);
      setActiveAiTask(null);
    }
  };

  return (
    <div className="flex h-screen bg-slate-100 text-slate-900 overflow-hidden font-sans">
      <aside className="w-[350px] flex flex-col bg-white border-r border-slate-200 shadow-xl z-10 shrink-0">
        <div className="p-4 border-b border-slate-100 flex justify-between items-center bg-blue-50/50">
          <div className="flex items-center gap-2">
            <div className="bg-blue-600 p-1.5 rounded-lg"><Layers className="w-5 h-5 text-white" /></div>
            <h1 className="font-bold text-lg text-slate-800 tracking-tight">雅韵排版 V2.0</h1>
          </div>
        </div>

        <div className="px-4 pt-3 pb-2 border-b border-slate-100 bg-slate-50">
          <div className="flex bg-slate-200/50 p-1 rounded-lg">
            <button onClick={() => setActiveTab('content')} className={`flex-1 flex justify-center items-center gap-1.5 py-1.5 text-xs font-medium rounded-md transition-colors ${activeTab === 'content' ? 'bg-white text-blue-600 shadow-sm' : 'text-slate-500 hover:text-slate-800'}`}>
              <FileText className="w-4 h-4" /> 内容编辑
            </button>
            <button onClick={() => setActiveTab('design')} className={`flex-1 flex justify-center items-center gap-1.5 py-1.5 text-xs font-medium rounded-md transition-colors ${activeTab === 'design' ? 'bg-white text-blue-600 shadow-sm' : 'text-slate-500 hover:text-slate-800'}`}>
              <Palette className="w-4 h-4" /> 美学设置
            </button>
            <button onClick={() => setActiveTab('ai')} className={`flex-1 flex justify-center items-center gap-1.5 py-1.5 text-xs font-medium rounded-md transition-colors ${activeTab === 'ai' ? 'bg-purple-600 text-white shadow-sm' : 'text-slate-500 hover:text-slate-800'}`}>
              <Sparkles className="w-4 h-4" /> AI中枢
            </button>
          </div>
        </div>

        <div className="flex-1 overflow-y-auto custom-scrollbar bg-slate-50 p-3">
          
          {activeTab === 'content' && (
            <div className="h-full flex flex-col">
              <div className="bg-blue-50 border border-blue-100 text-blue-800 text-[11px] p-2.5 rounded-lg mb-3 space-y-1">
                <p><strong>语法参考：</strong></p>
                <p>万能填空: <code>[答案]</code> (自动处理显隐)</p>
                <p>四线三格: <code>英[答案]</code> (自动生成空网格)</p>
                <p>强制换页: <code>====</code> (独占一行)</p>
                <p>分割线: <code>---</code> (独占一行)</p>
              </div>
              <div className="flex justify-between items-center mb-2">
                <span className="text-xs font-bold text-slate-700">Markdown 编辑器</span>
                <label className="flex items-center gap-1 px-2 py-1 bg-white border border-slate-200 text-slate-700 text-[11px] font-medium rounded hover:bg-slate-50 cursor-pointer shadow-sm transition-colors">
                  <Upload className="w-3 h-3" /> 导入 .md 文件
                  <input type="file" accept=".md,.txt" onChange={handleFileUpload} className="hidden" />
                </label>
              </div>
              <textarea 
                value={content} 
                onChange={(e) => setContent(e?.target?.value || '')} 
                className="flex-1 w-full resize-none rounded-lg border border-slate-200 bg-slate-900 p-3 font-mono text-[13px] leading-6 text-slate-100 focus:outline-none focus:border-blue-500 shadow-inner" 
              />
            </div>
          )}

          {activeTab === 'design' && (
            <div>
              {/* 版块 1: 雅韵排版 (母版库) */}
              <Accordion title="1. 雅韵排版 (母版库)" icon={<Layers className="w-4 h-4 text-blue-600"/>} defaultOpen={true}>
                <div className="space-y-3">
                  <SelectInput label="切换系统内置母版：" value={presetName} onChange={v => handleApplyPreset(v)} options={[
                    {label: '✨ 早读晚默版(墨绿)', value: 'morningDictation'},
                    {label: '✨ 核心词汇默写单(蓝)', value: 'coreDictation'}
                  ]}/>
                  <button onClick={handleRandomThemeColor} className="w-full flex justify-center items-center gap-1.5 text-[11px] bg-gradient-to-r from-blue-50 to-indigo-50 text-indigo-700 py-2 rounded border border-indigo-200 hover:opacity-80 transition-colors">
                    <Palette className="w-3 h-3" /> 🎨 一键智能调色 (更换教辅主题色)
                  </button>
                </div>
              </Accordion>

              {/* 版块 2: 页面格局与外框 */}
              <Accordion title="2. 页面格局与外框" icon={<LayoutTemplate className="w-4 h-4 text-blue-600"/>}>
                <div className="grid grid-cols-2 gap-3">
                  <SelectInput label="全局分栏" value={settings.globalColumns} onChange={v => set('globalColumns', Number(v))} options={[
                    {label: '单栏 (基础教案)', value: 1}, {label: '双栏 (紧凑)', value: 2}, {label: '三栏 (默写铺排)', value: 3},
                  ]}/>
                  <SelectInput label="页面外框" value={settings.paperBorder} onChange={v => set('paperBorder', v)} options={[
                    {label: '无边框', value: 'none'}, {label: '单实线', value: 'solid'}, {label: '单虚线', value: 'dashed'},
                    {label: '双实线', value: 'double'}, {label: '双层虚线卡片', value: 'double-dashed'},
                  ]}/>
                  <NumberInput label="智能分页 (每页最高题数)" value={settings.itemsPerPage} onChange={v=>set('itemsPerPage',v)} />
                  <div className="col-span-1"></div>
                  <NumberInput label="画布宽度" value={settings.paperWidth} onChange={v=>set('paperWidth',v)} />
                  <NumberInput label="画布高度(断页)" value={settings.paperHeight} onChange={v=>set('paperHeight',v)} />
                  <NumberInput label="上下边距" value={settings.paddingV} onChange={v=>set('paddingV',v)} />
                  <NumberInput label="左右边距" value={settings.paddingH} onChange={v=>set('paddingH',v)} />
                  <div className="col-span-2 flex items-center justify-between bg-slate-50 border border-slate-200 p-2 rounded mt-1">
                    <label className="text-xs font-medium text-slate-700">📜 底部显示页码</label>
                    <input type="checkbox" checked={settings.showPageNumber} onChange={e => set('showPageNumber', e?.target?.checked || false)} className="w-3.5 h-3.5 accent-blue-600" />
                  </div>
                </div>
              </Accordion>

              {/* 版块 3: 字体与字号设定 */}
              <Accordion title="3. 字体与字号设定" icon={<Type className="w-4 h-4 text-blue-600"/>}>
                <div className="grid grid-cols-2 gap-3">
                  <SelectInput label="大标题(H1)字体" value={settings.h1Font} onChange={v=>set('h1Font',v)} options={fontSelectOptions}/>
                  <NumberInput label="大标题(H1)字号" value={settings.h1Size} onChange={v=>set('h1Size',v)} />

                  <SelectInput label="一级标题(H2)字体" value={settings.h2Font} onChange={v=>set('h2Font',v)} options={fontSelectOptions}/>
                  <NumberInput label="一级标题(H2)字号" value={settings.h2Size} onChange={v=>set('h2Size',v)} />

                  <SelectInput label="二级标题(H3)字体" value={settings.h3Font} onChange={v=>set('h3Font',v)} options={fontSelectOptions}/>
                  <NumberInput label="二级标题(H3)字号" value={settings.h3Size} onChange={v=>set('h3Size',v)} />

                  <SelectInput label="扉页区(姓名/订正)字体" value={settings.metaFont} onChange={v=>set('metaFont',v)} options={fontSelectOptions}/>
                  <NumberInput label="扉页区(姓名/订正)字号" value={settings.metaSize} onChange={v=>set('metaSize',v)} />

                  <SelectInput label="重点词(格子)字体" value={settings.focusFont} onChange={v=>set('focusFont',v)} options={fontSelectOptions}/>
                  <NumberInput label="重点词字号" value={settings.focusSize} onChange={v=>set('focusSize',v)} />

                  <SelectInput label="正文字体" value={settings.baseFont} onChange={v=>set('baseFont',v)} options={fontSelectOptions}/>
              <NumberInput label="正文字号" value={settings.baseSize} onChange={v=>set('baseSize',v)} />
              
              <NumberInput label="行间距倍数" value={settings.lineHeight} step={0.1} onChange={v=>set('lineHeight',v)} />
              <NumberInput label="段落/网格间距(px)" value={settings.paragraphSpacing} onChange={v=>set('paragraphSpacing',v)} />
              
              <div className="col-span-2 flex items-center justify-between bg-slate-50 border border-slate-200 p-2.5 rounded-lg mt-1">
                <span className="text-[11px] font-bold text-slate-700">文字加粗控制</span>
                <div className="flex items-center gap-4">
                  <label className="flex items-center gap-1.5 cursor-pointer">
                    <input type="checkbox" checked={settings.baseBold || false} onChange={e=>set('baseBold', e.target.checked)} className="w-3.5 h-3.5 accent-blue-600"/>
                    <span className="text-[11px] text-slate-600">正文加粗</span>
                  </label>
                  <label className="flex items-center gap-1.5 cursor-pointer">
                    <input type="checkbox" checked={settings.focusBold !== false} onChange={e=>set('focusBold', e.target.checked)} className="w-3.5 h-3.5 accent-blue-600"/>
                    <span className="text-[11px] text-slate-600">重点词/答案加粗</span>
                  </label>
                </div>
              </div>
            </div>
          </Accordion>

          {/* 版块 4: 标题与重点装饰区 */}
              <Accordion title="4. 标题与重点装饰区" icon={<Heading className="w-4 h-4 text-blue-600"/>}>
                <div className="space-y-3">
                  <div className="p-2.5 bg-slate-50 border border-slate-200 rounded-lg space-y-2.5">
                    <div className="flex justify-between items-center border-b pb-1">
                      <div className="text-[11px] font-bold text-slate-700">H1 主标题装饰</div>
                      <label className="flex items-center gap-1 cursor-pointer">
                        <input type="checkbox" checked={settings.h1Bold !== false} onChange={e=>set('h1Bold', e.target.checked)} className="w-3 h-3 accent-blue-600"/>
                        <span className="text-[10px] text-slate-600">加粗</span>
                      </label>
                    </div>
                    <div className="grid grid-cols-2 gap-2">
                      <SelectInput label="对齐" value={settings.h1Align} onChange={v=>set('h1Align',v)} options={[{label:'居中',value:'center'},{label:'左对齐',value:'left'}]}/>
                      <SelectInput label="独立装饰" value={settings.h1Deco} onChange={v=>set('h1Deco',v)} options={commonDecoOptions}/>
                    </div>
                  </div>
                  <div className="p-2.5 bg-slate-50 border border-slate-200 rounded-lg space-y-2.5">
                    <div className="flex justify-between items-center border-b pb-1">
                      <div className="text-[11px] font-bold text-slate-700">H2 一级标题装饰</div>
                      <label className="flex items-center gap-1 cursor-pointer">
                        <input type="checkbox" checked={settings.h2Bold !== false} onChange={e=>set('h2Bold', e.target.checked)} className="w-3 h-3 accent-blue-600"/>
                        <span className="text-[10px] text-slate-600">加粗</span>
                      </label>
                    </div>
                    <div className="grid grid-cols-2 gap-2">
                      <SelectInput label="对齐" value={settings.h2Align} onChange={v=>set('h2Align',v)} options={[{label:'居中',value:'center'},{label:'左对齐',value:'left'}]}/>
                      <SelectInput label="独立装饰" value={settings.h2Deco} onChange={v=>set('h2Deco',v)} options={commonDecoOptions}/>
                    </div>
                  </div>
                  <div className="p-2.5 bg-slate-50 border border-slate-200 rounded-lg space-y-2.5">
                    <div className="flex justify-between items-center border-b pb-1">
                      <div className="text-[11px] font-bold text-slate-700">H3 二级标题装饰</div>
                      <label className="flex items-center gap-1 cursor-pointer">
                        <input type="checkbox" checked={settings.h3Bold !== false} onChange={e=>set('h3Bold', e.target.checked)} className="w-3 h-3 accent-blue-600"/>
                        <span className="text-[10px] text-slate-600">加粗</span>
                      </label>
                    </div>
                    <div className="grid grid-cols-2 gap-2">
                      <SelectInput label="对齐" value={settings.h3Align} onChange={v=>set('h3Align',v)} options={[{label:'居中',value:'center'},{label:'左对齐',value:'left'}]}/>
                      <SelectInput label="独立装饰" value={settings.h3Deco} onChange={v=>set('h3Deco',v)} options={commonDecoOptions}/>
                    </div>
                  </div>
                </div>
              </Accordion>

              {/* 版块 5: 品牌色彩库 */}
              <Accordion title="5. 品牌色彩库" icon={<PaintBucket className="w-4 h-4 text-blue-600"/>}>
                <div className="grid grid-cols-2 gap-3">
                  <ColorPicker label="全局正文色" value={settings.baseColor} onChange={v=>set('baseColor',v)} />
                  <ColorPicker label="大标题(H1)颜色" value={settings.h1Color} onChange={v=>set('h1Color',v)} />
                  <ColorPicker label="一级标题(H2)颜色" value={settings.h2Color} onChange={v=>set('h2Color',v)} />
                  <ColorPicker label="二级标题(H3)颜色" value={settings.h3Color} onChange={v=>set('h3Color',v)} />
                  <ColorPicker label="重点/四线格颜色" value={settings.focusColor} onChange={v=>set('focusColor',v)} />
                  <ColorPicker label="纸张底色(背景)" value={settings.paperBg} onChange={v=>set('paperBg',v)} />
                  <div className="col-span-2">
                    <ColorPicker label="外框/订正栏颜色" value={settings.paperBorderColor} onChange={v=>set('paperBorderColor',v)} />
                  </div>
                </div>
              </Accordion>

              {/* 版块 6: 水印与功能组件区 */}
              <Accordion title="6. 水印与功能组件区" icon={<Puzzle className="w-4 h-4 text-blue-600"/>}>
                <div className="bg-indigo-50 border border-indigo-100 p-2.5 rounded-lg space-y-2 mt-1">
                  <div className="flex items-center justify-between">
                    <label className="text-[11px] font-bold text-indigo-900 flex items-center gap-1">
                      <Sparkles className="w-3 h-3"/> Angie 品牌水印组件
                    </label>
                    <input type="checkbox" checked={settings.showBrand} onChange={e => set('showBrand', e?.target?.checked || false)} className="w-3.5 h-3.5 accent-indigo-600"/>
                  </div>
                  {settings.showBrand && (
                    <div className="flex items-center gap-2">
                      <span className="text-[10px] text-indigo-700">标签文本:</span>
                      <input type="text" value={settings.brandTag} onChange={e => set('brandTag', e?.target?.value || '')} className="flex-1 rounded border border-indigo-200 px-2 py-0.5 text-[11px] outline-none" />
                    </div>
                  )}
                </div>
                
                <div className="grid grid-cols-2 gap-2 mt-3">
                  <button onClick={() => insertSnippet('1. 测试内容\n   英[word]')} className="text-[11px] border border-slate-200 rounded py-1.5 hover:bg-slate-50 font-medium text-slate-700"> + 英语四线格 </button>
                  <button onClick={() => insertSnippet('1. 汉字注音\n   田[字](zì)')} className="text-[11px] border border-slate-200 rounded py-1.5 hover:bg-slate-50 font-medium text-slate-700"> + 汉字田字格 </button>
                </div>
              </Accordion>

              {/* 版块 7: 答案与题单生成 */}
              <Accordion title="7. 答案与题单生成" icon={<CheckSquare className="w-4 h-4 text-blue-600"/>} defaultOpen={true}>
                <div className="space-y-3">
                  <div className="bg-purple-50 p-3 rounded-lg border border-purple-100 space-y-3">
                    <h3 className="font-bold text-[11px] text-purple-900 flex items-center gap-1">
                      <Wand2 className="w-3 h-3 text-purple-600"/> 实时无损卷面切换
                    </h3>
                    <p className="text-[10px] text-purple-700 leading-tight">
                      💡 只需点击下方选项即可瞬间切换画布，绝不破坏左侧文本中填写的原答案！
                    </p>
                    <div className="flex flex-col gap-2 pt-1 border-t border-purple-200/50">
                       <label className="text-[11px] flex items-center gap-1.5 text-slate-700 cursor-pointer hover:bg-purple-100/50 p-1 rounded transition-colors">
                         <input type="radio" checked={examMode === 'student'} onChange={() => setExamMode('student')} className="accent-purple-600 w-3.5 h-3.5" /> 
                         <span className="font-medium">生成学生题单版</span> (自动留空)
                       </label>
                       <label className="text-[11px] flex items-center gap-1.5 text-slate-700 cursor-pointer hover:bg-purple-100/50 p-1 rounded transition-colors">
                         <input type="radio" checked={examMode === 'teacher'} onChange={() => setExamMode('teacher')} className="accent-purple-600 w-3.5 h-3.5" /> 
                         <span className="font-medium">生成教师解析版</span> (显示红色答案)
                       </label>
                    </div>
                  </div>

                  <div className="bg-white p-3 rounded-lg border border-slate-200 space-y-2 mt-2">
                    <h3 className="font-bold text-[11px] text-slate-800 flex items-center gap-1"><Code className="w-3 h-3 text-slate-600"/> 底版参数配置代码</h3>
                    <textarea 
                      value={jsonImport} onChange={e => setJsonImport(e?.target?.value || '')}
                      placeholder="点【导出】获取当前参数，或把旧参数粘贴于此点【汲取】..."
                      className="w-full h-16 text-[9px] font-mono p-1.5 border border-slate-200 rounded bg-slate-50 focus:outline-none custom-scrollbar"
                    />
                    <div className="flex gap-1.5">
                      <button onClick={handleExportJson} className="flex-1 py-1 text-[10px] font-medium bg-slate-800 text-white rounded hover:bg-slate-700">导出</button>
                      <button onClick={handleImportJson} className="flex-1 py-1 text-[10px] font-medium bg-blue-600 text-white rounded hover:bg-blue-700">汲取</button>
                    </div>
                  </div>
                </div>
              </Accordion>
            </div>
          )}

          {activeTab === 'ai' && (
            <div>
              {/* 版块 8: AI 智能副手 (Gemini API) */}
              <Accordion title="8. AI 智能副手 (Gemini)" icon={<Sparkles className="w-4 h-4 text-blue-600"/>} defaultOpen={true}>
                <div className="space-y-3">
                  <div className="bg-gradient-to-br from-indigo-50 to-purple-50 p-3 rounded-lg border border-indigo-100 space-y-3 shadow-inner">
                    <h3 className="font-bold text-[11px] text-indigo-900 flex items-center gap-1">
                      <Wand2 className="w-3 h-3 text-indigo-600"/> 基于大模型的语料加工
                    </h3>
                    <p className="text-[10px] text-indigo-700 leading-tight">
                      丢掉繁琐的手动排版！粘贴任意杂乱的文本或课文，让 AI 为您一键生成专业的教辅题型。
                    </p>
                    <div className="flex flex-col gap-2 pt-1">
                      <button onClick={() => handleAiAction('smart_format')} disabled={isGenerating} className="w-full flex justify-center items-center gap-1.5 text-[11px] bg-white text-indigo-700 py-1.5 rounded border border-indigo-200 hover:bg-indigo-50 transition-colors shadow-sm disabled:opacity-50">
                        {activeAiTask === 'smart_format' ? <Loader2 className="w-3 h-3 animate-spin"/> : <Sparkles className="w-3 h-3 text-yellow-500" />}
                        ✨ 杂乱单词 一键排版清洗
                      </button>
                      <button onClick={() => handleAiAction('extract_reading')} disabled={isGenerating} className="w-full flex justify-center items-center gap-1.5 text-[11px] bg-white text-indigo-700 py-1.5 rounded border border-indigo-200 hover:bg-indigo-50 transition-colors shadow-sm disabled:opacity-50">
                        {activeAiTask === 'extract_reading' ? <Loader2 className="w-3 h-3 animate-spin"/> : <Sparkles className="w-3 h-3 text-blue-500" />}
                        ✨ 英语短文 一键提取生词本
                      </button>
                      <button onClick={() => handleAiAction('generate_sentences')} disabled={isGenerating} className="w-full flex justify-center items-center gap-1.5 text-[11px] bg-indigo-600 text-white py-1.5 rounded border border-indigo-700 hover:bg-indigo-700 transition-colors shadow-sm disabled:opacity-50">
                        {activeAiTask === 'generate_sentences' ? <Loader2 className="w-3 h-3 animate-spin"/> : <Sparkles className="w-3 h-3 text-yellow-300" />}
                        ✨ 核心词汇 一键生成语境填空题
                      </button>
                      <button onClick={() => handleAiAction('smart_fill')} disabled={isGenerating} className="w-full flex justify-center items-center gap-1.5 text-[11px] bg-emerald-600 text-white py-1.5 rounded border border-emerald-700 hover:bg-emerald-700 transition-colors shadow-sm disabled:opacity-50 mt-2">
                        {activeAiTask === 'smart_fill' ? <Loader2 className="w-3 h-3 animate-spin"/> : <Sparkles className="w-3 h-3 text-emerald-300" />}
                        ✨ 保持题干不变：自动把下划线转为红字答案
                      </button>
                    </div>
                  </div>
                </div>
              </Accordion>
            </div>
          )}

        </div>
      </aside>

      <main className="flex-1 flex flex-col bg-slate-200/60 p-4 relative overflow-hidden">
        <div className="absolute top-4 left-4 right-4 flex justify-between items-center z-10 pointer-events-none">
          <div className="flex items-center gap-2 bg-white/90 backdrop-blur px-3 py-1.5 rounded-lg border border-slate-200 shadow-sm pointer-events-auto">
            <Eye className="w-4 h-4 text-slate-500" />
            <span className="text-xs font-bold text-slate-700">实时渲染视图</span>
          </div>

          <div className="flex items-center gap-2 pointer-events-auto">
            <div className="flex items-center gap-1 bg-white/90 px-1 py-1 rounded-lg border border-slate-200 shadow-sm">
              <button onClick={() => set('zoom', Math.max(30, settings.zoom - 5))} className="w-6 h-6 flex justify-center items-center rounded hover:bg-slate-100 text-slate-600">-</button>
              <span className="w-9 text-center text-xs font-medium text-slate-700">{settings.zoom}%</span>
              <button onClick={() => set('zoom', Math.min(150, settings.zoom + 5))} className="w-6 h-6 flex justify-center items-center rounded hover:bg-slate-100 text-slate-600">+</button>
            </div>
            
            <button onClick={handleExportImage} className="flex items-center gap-1.5 px-3 py-1.5 bg-[#2b579a] text-white text-xs font-medium rounded-lg hover:bg-[#1e3f73] shadow-md transition-all">
              {isGenerating ? <Loader2 className="w-3.5 h-3.5 animate-spin"/> : <ImageIcon className="w-3.5 h-3.5" />} 
              导出高清图
            </button>
            <button onClick={handlePrint} className="flex items-center gap-1.5 px-3 py-1.5 bg-emerald-600 text-white text-xs font-medium rounded-lg hover:bg-emerald-700 shadow-md">
              <FileDown className="w-3.5 h-3.5" /> 打印为 PDF
            </button>
          </div>
        </div>

        <div className="flex-1 mt-12 overflow-auto custom-scrollbar pt-4 pb-12 flex justify-center items-start">
          <div style={{ transform: `scale(${settings.zoom / 100})`, transformOrigin: 'top center', transition: isExporting ? 'none' : 'transform 0.2s ease-out' }}>
            <style dangerouslySetInnerHTML={{ __html: previewCss }} />
            <div 
              className="paper-root" 
              dangerouslySetInnerHTML={{ __html: renderedContent }} 
            />
          </div>
        </div>
      </main>
    </div>
  );
}





