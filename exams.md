1. (A)請寫一個程式把裡面的字串反過來。

    (B)請寫一個程式把裡面的字串,每個單字本身做反轉,但是單字的順序不變。

```
f("junyiacademy") == "ymedacaiynuj"
f("flipped class room is important") == "deppilf ssalc moor si tnatropmi"
```

Ans:


(A)
```javascript
const reverse = (str) => {
    let tmp = '', boundary = str.length - 1
    for(let i = 0; i <= boundary; i++) {
        tmp += str[boundary - i]
    }

    return tmp
}
```

(B)
```javascript 
const reverseStr = (str) => {
    let tmp = '', boundary = str.length - 1
    for(let i = 0; i <= boundary; i++) {
        tmp += str[boundary - i]
    }

    return tmp
}

const reverseSentence = (str) => {
    let tmp = '', source = str.split(' ')

    return source.reduce((acc, cur) => {
        return [...acc, reverseStr(cur)]
    }, []).join(' ')
}
```

2. 請寫一個程式,Input 是一個數字,Output 是從 1 到這個數字,扣除掉所有 3 的
倍數以及 5 的倍數,但是需要保留同時是 3 和 5 的倍數的總數字數。

```
Input:15
所有的數字是:1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15
其中 3, 6, 9, 12 被剔除;5, 10 被剔除;但是 15 被保留
所以剩下來的數字是 1, 2, 4, 7, 8, 11, 13, 14, 15,因此
Output:9
```

Ans: 
```javascript
const filterSum = (n) => {
    let result = 0
    for(let i = 1; i <= n; i++) {
        const isMultiple3 = i % 3 === 0, isMultiple5 = i % 5 === 0
        if((isMultiple3 && isMultiple5) || (!isMultiple3 && !isMultiple5)) {
            result += 1
        }
    }

    return result
}
```

3. 房間裡有三個袋子,一個只裝鉛筆,一個只裝原子筆,第三個有鉛筆也有原子筆。
袋子是不透明的,單從袋子的外表上看不出任何差異,你不知道哪個袋子裝什麼。
除了袋子上各貼了一個標示("鉛筆"、"原子筆"、"混和"),且標示都是錯的
(e.g. 標示鉛筆的袋子可能是混和的或是只裝原子筆)。
你只能選一個袋子,拿出裡面一支筆,看是鉛筆還是原子筆,然後你要推論出這三
個袋子分別的情況。請列出你的作法,以及解釋為什麼這樣可以找到答案。

Ans: 

挑選標示為混合的


假設拿出來是鉛筆，則代表混合這袋其實是只裝鉛筆，接著判斷標示為鉛筆的袋子，目前剩下兩種可能性：混合、原子筆，由於另外一袋標示原子筆，如果標示為鉛筆的這袋是混合的話，那另一袋的標示就是正確的(但題目說標示都是錯的)，所以標示為鉛筆這袋只可能是只裝原子筆，而標示為原子筆的袋子則為混合



4. 有三個人一起到迪士尼遊玩,中午肚子餓了,去餐廳點了一份現在最夯的冰雪奇緣
雙人組,要價 900 元,付錢後,服務生發現今天套餐大特價,只要 750 元,因此
服務生應該退還 150 元給這三個人,但是這位服務生一時鬼迷心竅,決定暗槓 60
元,只退了 90 元給這三個遊客。
那麼:三人各出 300 元 - 服務生還給他們一人 30 元 = 三人各出 270 元。
270元 × 3 人+ 服務生私吞的 60 元 = 810 + 60 = 870 !? 怎麼不是 900 元呢?還
有 30 元去哪了呢?請用敘述的方式,儘量清楚解釋問題出在哪裡。


Ans:

計算公式有誤

套餐大特價後只要750
三人各出250 + 服務生退還一人30 = 三人各出280。
280 x 3 人 + 服務生私吞的60 = 840 + 60 = 900

如果反過來用扣的話基準點不應該為900
原價900，特價750，加上服務生私吞的60，因此一共只拿出810
三人各出300 - 服務生還給一人30 = 270，270 x 3人 = 810
