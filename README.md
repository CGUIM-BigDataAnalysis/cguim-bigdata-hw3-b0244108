長庚大學 大數據分析方法 作業三
================

網站資料爬取
------------

``` r
library(rvest)
```

    ## Loading required package: xml2

``` r
ptt <- "https://www.ptt.cc/bbs/Tech_Job/index.html"
ptt_data = c()
for( i in 1:10){
  ptt_title <- read_html(ptt) %>% html_nodes(".title") %>% html_text
  ptt_pushnum <- read_html(ptt) %>% html_nodes(".nrec") %>% html_text
  ptt_author <- read_html(ptt) %>% html_nodes(".author") %>% html_text
  pttcon <- data.frame(title = ptt_title,num = ptt_pushnum,author = ptt_author) 
  ptt_data <- rbind(ptt_data,pttcon)
  ptt_link <- read_html(ptt) %>% html_node(".btn-group-paging a:nth_child(2)") %>% html_attr("href")
  ptt<-paste0('https://www.ptt.cc',ptt_link)
}
```

爬蟲結果呈現
------------

``` r
knitr::kable(
  ptt_data[c("title","num","author")])
```

| title                                                       | num | author       |
|:------------------------------------------------------------|:----|:-------------|
| Re: \[討論\] 台積電VS中油                                   | 4   | tomtowin     |
| \[請益\] 台積vs世界                                         | 33  | q7w8s5       |
| \[請益\] 暑期實習請益                                       | 4   | quasi        |
| Fw: \[台北\] 推手媒體誠徵後端工程師                         |     | ssmartdan841 |
| \[請益\] 面試邀約寄信要你回撥?                              | 1   | sheu123      |
| \[請益\] Offer請益(仁寶/緯創)                               | 2   | johnnypk321  |
| \[新聞\] 台積i8單 下月量產                                  |     | unrest       |
| \[討論\] 聯穎光電面試                                       |     | key9028      |
| 律師為您解惑－線上勞動法免費諮詢即日為勞工 … 爆             | pz  | s            |
| \[公告\] Tech\_Job板板規 2014.03.01                         | 7   | mmkntust     |
| \[公告\] 置底 檢舉/推薦 文章                                | 爆  | mmkntust     |
| \[免費\]工作人生顧問                                        | 爆  | zodiac       |
| 捷普 綠點刀具                                               | 3   | tn372845     |
| \[請益\] 日商安立知                                         | 3   | pjc202       |
| \[情報\] 蘋果申請具備iPhone核心之Macbook產品                | 6   | zxcvxx       |
| \[請益\]有人收到德州儀器技術行銷工程師面試邀請?             | 2   | wer11        |
| \[請益\] 請問陸資的IC設計公司                               | 7   | DigiTalent   |
| \[請益\] 德州儀器設備工程師實習                             | 2   | oeys         |
| \[討論\] 國家光電好嗎                                       |     | chag06       |
| Re: \[請益\] 請問陸資的IC設計公司                           | 16  | DigiTalent   |
| \[請益\] 是否該調往偏鄉工作？                               | 42  | NakiXIII     |
| \[請益\] 校園徵才請益                                       | 5   | lponnn       |
| \[請益\] 關於科技業或是保險                                 | 1   | dfg512       |
| \[請益\] Advantest二手設備商                                | 3   | CA42         |
| Fw: \[請益\] 夜間進修                                       |     | neon2102     |
| \[請益\] 華通電腦                                           | 6   | jackjack0805 |
| \[討論\] 矽品好像沒有板上說的那麼不好吧~                    | 49  | goodlike     |
| \[討論\] 試用期超過三個月                                   | 12  | ScrewYou     |
| \[討論\] 台積電VS中油                                       | 8   | ej4g4        |
| \[請益\] 元晶太陽能                                         | 1   | p4818046     |
| \[請益\] 金屬工業中心面試                                   |     | huaygina     |
| \[請益\] 在職碩班選擇請益，中興vs中央                       | 1   | AKFG         |
| 敬鵬-資訊系統開發管理師                                     | 1   | incoterms    |
| \[請益\] 美亞科技                                           | 6   | key9028      |
| \[新聞\] 總經理巡廠要整理桌面　群創員工爆比當兵             | 35  | zzzz8931     |
| Re: \[討論\] 關於機台零件是不是都撐到最後？                 | 1   | c1823akimo   |
| 創群科技                                                    | 12  | jamiefly     |
| \[討論\] 有人因為辦公室太舊太髒離職的嗎??                   | 43  | yamakazi     |
| (本文已被刪除) \[VamYU\]                                    | 12  | -            |
| Re: \[心得\] 我在拓凱(台中工業區)的日子                     | 6   | simplep2002  |
| Re: \[新聞\]【台GG別走動畫】台積傳將赴美砸5千億建3          | 2   | egnaro123    |
| \[聘書\] 緯創/建漢/帆宣                                     | 3   | tomandjim    |
| (本文已被刪除) \[piggg\]                                    |     | -            |
| \[徵才\] 交大電子所誠徵碩士級研究助理                       | 1   | xgin         |
| \[情報\] 國網中心擴大舉辦工讀生/實習生徵才活動              |     | ZhaoYun      |
| \[請益\] 亞太國際電機 製程 疑問                             |     | ian00727     |
| \[徵才\] 掃描器/光學元件/韌體工程師 BioInspira, Inc         |     | Herc         |
| \[請益\] 漢民MFGP CNC 新竹                                  | 1   | Crosswise    |
| Re: \[心得\]小寶跟大寶 真的不一樣                           | 22  | ikeru        |
| Re: \[請益\] Offer請益 英業達/鴻海                          | 1   | wer11        |
| (本文已被刪除) \[pjc202\]                                   |     | -            |
| Re: \[請益\] 陶氏化學CDP面試詢問                            | 4   | piggg        |
| (已被mmkntust刪除) <sht255>                                 | 10  | -            |
| ［疑惑］台GG要在竹南設廠的傳聞有下文嗎？                    | 38  | q99518g      |
| \[聘書\] Offer請益 達創/新日興                              | 12  | lovetire     |
| \[請益\] Offer請益 英業達/鴻海                              | 34  | kusahara     |
| \[請益\] 聯電職務請益                                       | 11  | blacktea0930 |
| \[請益\] offer請益 garmin自動化機構/國外sales               | 8   | Blueicex     |
| \[面試\] 友達晶材IE面試與錄取                               | 12  | nick800418   |
| (本文已被刪除) \[pptgov\]                                   |     | -            |
| \[請益\] offer 選擇(美光vs力晶）                            | 42  | chsweet      |
| Fw: \[請益\] 科技工程師練英文                               | 5   | ggggggh      |
| \[請益\] offer 上無註明保障年月薪                           | 26  | ck49         |
| \[心得\] 面試心得(乾坤/正新/台灣荏原/Lam/)                  | 8   | Sorry5566    |
| \[徵才\] 汐止-徵求會PHP與SQL的工程師                        | 8   | MobileMan    |
| \[請益\] 頎邦科技                                           | 1   | popularman   |
| \[面試\] 台達化學公司(前鎮廠) 工作環境與福利                | 5   | tcl2830      |
| \[請益\] 點晶科技 推嗎                                      | 5   | okmijnuhb    |
| (本文已被刪除) \[tcl2830\]                                  |     | -            |
| \[心得\] 面試心得(基恩斯/精材/ASML/艾克爾)                  | 28  | Sorry5566    |
| \[請益\] offer選擇(虹晶 vs 小豬屎屋)                        | 6   | Kovainen     |
| (本文已被刪除) \[nntn\]                                     | 3   | -            |
| \[徵才\] ucfunnel-媒體開發/PM/Node.js/Frontend              | 1   | livingroom   |
| \[請益\] 第一份工作薪水重要還是練功重要?                    | 爆  | s6307        |
| Re: \[請益\] 覆晶封裝製程轉職問題                           | 6   | gnh1021      |
| \[請益\] 研發替代役                                         | 6   | leo710215    |
| \[請益\]offer選擇                                           | 10  | david597     |
| \[心得\] 面試 大立光電/艾克爾/采鈺/百佳泰/美光              | 11  | goodboy8899  |
| \[請益\] 電機女生找工作                                     | 74  | alice2520200 |
| \[心得\] 我在拓凱(台中工業區)的日子                         | 71  | dash0804     |
| Re: \[心得\] 群聯不舒服的面試經驗                           | 10  | magic704226  |
| (本文已被刪除) \[catdogter\]                                | 31  | -            |
| (已被mmkntust刪除) <stan1111> 版規六                        |     | -            |
| \[請益\] 內湖緯創ＥＢＧ情況                                 | 11  | wort         |
| \[請益\] 在台灣工作未來方向                                 | 15  | omega0210    |
| \[請益\] 陶氏化學CDP面試詢問                                | 7   | chengyuche   |
| \[請益\] 做Power ICdesign的前景？                           | 29  | golover      |
| \[討論\] 關於機台零件是不是都撐到最後？                     | 21  | s4001        |
| \[討論\] 關於伺服器代工                                     | 15  | orz3qonz     |
| \[請益\] 請問有人了解三浦鍋爐嗎                             | 2   | skatopia     |
| \[新聞\]【台GG別走動畫】台積傳將赴美砸5千億建3              | 44  | DickMartin   |
| \[新聞\] 靠文青打敗台積電　新鮮人最嚮往企業出爐             | 58  | popoallan    |
| \[請益\] 哪條路，若想轉職比較方便？                         | 10  | a40232145    |
| \[請益\] 戀人最近在忙什麼？                                 | 15  | leatica      |
| \[請益\] 想詢問面試狀況                                     | 1   | howdai123    |
| \[新聞\] 鐵血CEO蔡力行扮「殺手」？聯發科員工剉              | 48  | tw689        |
| \[請益\] 業務工程師 北區推薦                                | 7   | praive       |
| \[新聞\] 首年享13天特休！德州儀器徵100人　研究所畢起薪5-6萬 | 10  | wer11        |
| \[新聞\] 國防55級分 畢業「免當軍人」上班月領51K             | 4   | s6307        |
| \[新聞\] 科技RD「每天7點下班」超貼心　台女竟怒              | X1  | AK47shoot    |
| Re: \[新聞\] 科技RD「每天7點下班」超貼心　台女              | 2   | join183club  |
| \[心得\] 群聯不舒服的面試經驗                               | 49  | wears        |
| \[討論\] 面試有補助交通費的有那些公司?                      | 43  | magic704226  |
| \[新聞\] 聯發科Q1營業淨利恐季減70%                          | 38  | unrest       |
| \[請益\] offer選擇 力晶/景碩                                | 4   | blacksky124  |
| Re: \[公司\] 大船集團-達航科技                              |     | pinkowa      |
| \[請益\] 系統廠HW 能轉甚麼職缺?                             | 9   | sustaned     |
| \[聘書\] offer請益 華碩/彩富/矽創                           | 8   | wuhalala     |
| \[請益\] 正文是屬於ic design的公司嗎？                      |     | ghost1006    |
| \[請益\] 請問日本還有能打的半導體廠嗎                       | 9   | lin214       |
| \[請益\] 覆晶封裝製程轉職問題                               | 15  | KFCNTU       |
| \[新聞\] 華爾街日報：印度即將開始生產iPhone                 | 3   | Lanaroh      |
| \[請益\] 大公司的APR 跟小公司的數位IC                       | 17  | qqr29        |
| \[心得\] AMAT/Ultratech/mattson/Rudolph/ASM                 | 25  | roy10531     |
| Fw: \[公司\] 大船集團-達航科技                              | 3   | Miwaitte     |
| \[請益\] 仁寶 智慧型裝置 android                            | 12  | jenny920218  |
| \[請益\] 台汽電公司待遇及福利如何                           | 2   | s357678      |
| Re: \[討論\] 台塑or中油                                     | 20  | turn329      |
| \[新聞\] 蔡力行轉戰聯發科 網友：員工苦日子到                | 22  | cychine      |
| \[請益\] 聯電/美光/友達 選擇                                | 37  | suryany      |
| \[請益\] 環球水泥與耐落螺絲                                 | 7   | e3472419     |
| Re: \[請益\] 仁寶 智慧型裝置 android                        | 3   | ABCcomputer  |
| \[請益\] 南科 新世紀光電公司好嗎??                          | 6   | zgmfx0326    |
| Re: \[請益\] 環球水泥與耐落螺絲                             | 4   | giggled      |
| \[討論\] 要求先提供照片 涉及違反就服法???                   |     | seedhyper    |
| Re: \[請益\]信鼎技術 面試前準備?                            |     | AlioAlio     |
| \[請益\] 克達科技(安捷倫電子量測儀器代理)                   | 2   | dmgucci      |
| \[新聞\] 蔡力行轉戰聯發科 台積電發表看法了                  | 29  | kof70380     |
| \[請益\]請問威剛的工作狀況                                  | 4   | rock913343   |
| \[討論\] 美商Ubiquiti Networks優比快                        | 10  | aaron2034b   |
| Re: \[討論\] 鈞立科技(最新力作再現)                         | 1   | lkklkksppspp |
| \[請益\] C++有沒有類似SCJP的題庫                            | 5   | Nippey       |
| Re: \[討論\] 台積電有可能成為百年企業嗎 ?                   | 6   | bluejade1235 |
| \[新聞\] 聯詠員工分紅打6折 群聯大方送5.5億增1成             | 6   | gn01216674   |
| \[討論\]報到的第二個禮拜想離職.......                       | 8   | judy79702    |
| Re: \[討論\]報到的第二個禮拜想離職.......                   | 56  | join183club  |
| \[面試\] 在linkedin上找工作 就不會被原公司發現?             | 5   | sustaned     |
| \[請益\] 錄取未報到..                                       |     | qqdnsr       |
| \[請益\] 首岳資訊網路股份有限公司                           |     | edison81630  |
| Re: \[討論\] 台積電有可能成為百年企業嗎 ?                   | 8   | lovebridget  |
| 長春彰濱廠                                                  | 6   | adidasshow   |
| \[情報\] 英特爾購併Mobileye是追夢還是夢靨？                 | 6   | zxcvxx       |
| Re: \[討論\]報到的第二個禮拜想離職.......                   | 6   | hidog        |
| Re: \[討論\]報到的第二個禮拜想離職.......                   |     | pinkowa      |
| \[請益\] 鴻勝化學&宏騰光電...                               | 3   | qqming0721   |
| \[討論\] 台塑or中油                                         | 79  | Mason61931   |
| \[新聞\] 蔡力行轉戰聯發科 網友：員工苦日子到                | 38  | jeromeshih   |
| \[請益\] 英業達Server的power team                           | 4   | middux       |
| \[討論\] 中部某封測廠的面談經驗                             | 8   | stennis      |
| \[新聞\] 【震驚科技業】蔡力行轉戰聯發科　是否               | 36  | wahaha23     |
| \[請益\] 奇美材料到底好不好= =                              | 13  | esp0122      |
| \[請益\] 力晶元件助理工程師                                 | 12  | PTT1774      |
| Re: \[新聞\] 傳蔡力行 跳槽聯發科(已公告)                    | 15  | TSMCer       |
| \[請益\] 友達 美光 力晶 哪家最推薦去呢?                     | 45  | okopp        |
| \[請益\] 面試請益                                           | 3   | lhx63524     |
| 資料探勘及資料分析的基本能力為何                            |     | uasalada     |
| \[請益\] 元隆電子                                           | 2   | zyxcba5      |
| \[請益\] FAE面試請益                                        | 30  | lovelyjojo   |
| Re: \[新聞\] 聯發科宣布 蔡力行接共同執行長、集團副          | 14  | a875979      |
| \[請益\] 晶電 vs 鼎元 (竹南)                                | 9   | kkkmaxtine   |
| \[討論\] 晶睿通訊                                           | 5   | tiyico       |
| \[請益\] gg設備幹到頂天有機會被高薪挖角嗎                   | 4   | onlytiger    |
| \[討論\] 新人離職                                           | 73  | forgood      |
| \[請益\]男生做友達OP 適合待到退休嗎?                        | 18  | Silent       |
| \[討論\] 陣亡率高/免洗的職位                                | 25  | NTUlosers    |
| \[討論\] 科技業公司一虧損就開始拆子公司是常態嗎             | 14  | gotptt       |
| \[徵才\] Taylormade Golf company (高雄辦公室)               |     | loddy        |
| \[討論\] 台積電有可能成為百年企業嗎 ?                       | 9   | goodpoint    |
| \[請益\]華新科福利                                          | 4   | ichior       |
| \[請益\] 緯創server部門好嗎?                                | 8   | fantacy0225  |
| \[請益\] 尋求找工作方向建議                                 | 2   | YWEC         |
| \[新聞\] 聯發科訂單沒跟上                                   | 3   | unrest       |
| \[請益\] 走品質的有可能年薪破百嗎?                          | 21  | DUFA         |
| \[討論\] 板上有人遇過這種情況嗎                             | 4   | forgetwhat   |
| \[請益\] 在台灣只剩下一年 該換工作嗎?                       | 9   | kissyourbi   |
| \[情報\] (代po)科技人面試求職講座                           | 6   | yunnnn       |
| Re: \[請益\]信鼎技術 面試前準備?                            | 7   | AlioAlio     |
| Re: \[新聞\] 斥資600億 「綠能科學城」落腳台南沙崙           | 13  | juangpeiyi   |
| \[請益\] offer 選擇                                         | 6   | eclipse911   |
| \[討論\] 系統廠的生命力是否比較強？                         | 8   | join183club  |
| \[請益\] 有人聽過Sogeti這間公司嗎                           | 1   | takeon       |
| \[請益\] offer 選擇                                         | 1   | chrishyper   |
| \[新聞\] 「中國製造2025」美憂威脅國安                       | 12  | AAAB         |
| \[請益\] 菱X科技                                            | 10  | maxgxking    |
| \[新聞\] 環評空污缺電 黃士修：台積電快走吧!                 | 31  | wahaha23     |
| \[請益\] htc派遣問題                                        |     | seal44       |
| \[新聞\] 傳蔡力行 跳槽聯發科(已公告)                        | 53  | http405      |
| Re: \[新聞\] 傳蔡力行 跳槽聯發科                            | 10  | jeromeshih   |
| \[新聞\] 聯發科宣布 蔡力行接共同執行長、集團副              | 72  | RTA          |
| Re: \[請益\] Nvidia的Android Framework/SW Engineer          | 5   | nixt         |
| \[請益\] 敏實集團 minth group                               | 1   | urocissa     |
| \[聘書\] 研替offer詢問(QNAP/緯創)                           | 5   | lebron0426   |

解釋爬蟲結果
------------

``` r
str(ptt_data)
```

    ## 'data.frame':    192 obs. of  3 variables:
    ##  $ title : Factor w/ 186 levels "\n\t\t\t\n\t\t\t\t[公告] 置底 檢舉/推薦 文章\n\t\t\t\n\t\t\t",..: 12 6 5 11 4 7 9 8 10 2 ...
    ##  $ num   : Factor w/ 50 levels "","1","2","33",..: 5 4 5 1 2 3 1 1 7 6 ...
    ##  $ author: Factor w/ 166 levels "johnnypk321",..: 9 5 6 8 7 1 10 2 4 3 ...

爬到190筆資料

``` r
a<-table(ptt_data$author)
sort(a)
```

    ## 
    ##  johnnypk321          pzs       q7w8s5        quasi      sheu123 
    ##            1            1            1            1            1 
    ## ssmartdan841     tomtowin       zodiac         AKFG         CA42 
    ##            1            1            1            1            1 
    ##       chag06       dfg512        ej4g4     goodlike     huaygina 
    ##            1            1            1            1            1 
    ## jackjack0805       lponnn     NakiXIII     neon2102         oeys 
    ##            1            1            1            1            1 
    ##     p4818046       pjc202     ScrewYou     tn372845   c1823akimo 
    ##            1            1            1            1            1 
    ##    Crosswise    egnaro123         Herc     ian00727        ikeru 
    ##            1            1            1            1            1 
    ##    incoterms     jamiefly        piggg  simplep2002    tomandjim 
    ##            1            1            1            1            1 
    ##         xgin     yamakazi      ZhaoYun     zzzz8931 blacktea0930 
    ##            1            1            1            1            1 
    ##     Blueicex      chsweet         ck49      ggggggh     Kovainen 
    ##            1            1            1            1            1 
    ##     kusahara     lovetire    MobileMan   nick800418    okmijnuhb 
    ##            1            1            1            1            1 
    ##   popularman      q99518g      tcl2830 alice2520200   chengyuche 
    ##            1            1            1            1            1 
    ##     dash0804     david597   DickMartin      gnh1021      golover 
    ##            1            1            1            1            1 
    ##  goodboy8899    leo710215   livingroom    omega0210     orz3qonz 
    ##            1            1            1            1            1 
    ##    popoallan        s4001     skatopia         wort    a40232145 
    ##            1            1            1            1            1 
    ##    AK47shoot  blacksky124    ghost1006    howdai123       KFCNTU 
    ##            1            1            1            1            1 
    ##      Lanaroh      leatica       lin214       praive        tw689 
    ##            1            1            1            1            1 
    ##        wears     wuhalala   aaron2034b  ABCcomputer      cychine 
    ##            1            1            1            1            1 
    ##      dmgucci     e3472419      giggled  jenny920218     kof70380 
    ##            1            1            1            1            1 
    ## lkklkksppspp     Miwaitte       Nippey        qqr29   rock913343 
    ##            1            1            1            1            1 
    ##     roy10531      s357678    seedhyper      suryany      turn329 
    ##            1            1            1            1            1 
    ##    zgmfx0326   adidasshow bluejade1235  edison81630      esp0122 
    ##            1            1            1            1            1 
    ##   gn01216674        hidog    judy79702  lovebridget   Mason61931 
    ##            1            1            1            1            1 
    ##       middux      PTT1774       qqdnsr   qqming0721      stennis 
    ##            1            1            1            1            1 
    ##      a875979  fantacy0225      forgood    goodpoint       gotptt 
    ##            1            1            1            1            1 
    ##       ichior   kkkmaxtine     lhx63524        loddy   lovelyjojo 
    ##            1            1            1            1            1 
    ##    NTUlosers        okopp    onlytiger       Silent       tiyico 
    ##            1            1            1            1            1 
    ##       TSMCer     uasalada         YWEC      zyxcba5         AAAB 
    ##            1            1            1            1            1 
    ##   chrishyper         DUFA   eclipse911   forgetwhat      http405 
    ##            1            1            1            1            1 
    ##   juangpeiyi   kissyourbi   lebron0426    maxgxking         nixt 
    ##            1            1            1            1            1 
    ##          RTA       seal44       takeon     urocissa       yunnnn 
    ##            1            1            1            1            1 
    ##      key9028     mmkntust   DigiTalent       zxcvxx    Sorry5566 
    ##            2            2            2            2            2 
    ##  magic704226        s6307      pinkowa     sustaned     AlioAlio 
    ##            2            2            2            2            2 
    ##   jeromeshih     wahaha23       unrest        wer11  join183club 
    ##            2            2            3            3            3 
    ##            - 
    ##            9

最多發文者為（被刪除文章）有9筆資料，但是沒有作者名稱，所以找次高的為3次發文的作者有wer11和 join183club作者。

打關鍵字台積電的搜尋，發現有人把台積電簡稱為台GG。
