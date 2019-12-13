# 使用

## 顯示

### ◇ 格式化時間

```javascript
moment().format('MMMM Do YYYY, h:mm:ss a'); // December 13th 2019, 12:01:18 pm
moment().format('dddd');                    // Friday
moment().format("MMM Do YY");               // Dec 13th 19
moment().format('YYYY [escaped] YYYY');     // 2019 escaped 2019
moment().format();                          // 2019-12-13T12:01:18+08:00
```

### ◇ 相對時間

```javascript
moment("20111031", "YYYYMMDD").fromNow(); // 8 years ago
moment("20120620", "YYYYMMDD").fromNow(); // 7 years ago
moment().startOf('day').fromNow();        // 12 hours ago
moment().endOf('day').fromNow();          // in 12 hours
moment().startOf('hour').fromNow();
```

### ◇ 日歷時間

```javascript
moment().subtract(10, 'days').calendar(); // 12/03/2019
moment().subtract(6, 'days').calendar();  // Last Saturday at 12:00 PM
moment().subtract(3, 'days').calendar();  // Last Tuesday at 12:00 PM
moment().subtract(1, 'days').calendar();  // Yesterday at 12:00 PM
moment().calendar();                      // Today at 12:00 PM
moment().add(1, 'days').calendar();       // Tomorrow at 12:00 PM
moment().add(3, 'days').calendar();       // Monday at 12:00 PM
moment().add(10, 'days').calendar();      // 12/23/2019
```

## 驗證時間

驗證時間可以用在確認時間是否為有效的時間，或是是否有在設定的時間以內

### EX

驗證是否有在一段時間以內或是在截止日以前

```javascript
moment('要驗證的日期').isBetween('起始日', '截止日'); // true or false
moment('2018-11-02').isBetween('2018-11-01', '2018-11-13'); // true
moment('2010-10-20').isBefore('2010-10-19'); // false
```

## 運算

moment.js 可以運算時間，像是取出時間的最大值，或是增加天數。

### EX

現在的日期加上七天

```javascript
moment().add(7, 'days'); // Thu Dec 20 2019 17:25:31 GMT+0800
```

現在的日期加上七天再加上一個月（鏈式寫法）

```javascript
moment().add(7, 'days').add(1, 'months'); // Mon JAN 20 2020 17:26:28 GMT+0800
```

第二個例子是找出這個陣列中，日期最大的，這邊要注意的是，日期最大的也就是最接近現在的，相對於年齡來說就是最小的。不只有 max 可以使用，min 也同樣可以被使用

```javascript
var friends = [{name: 'Angel', birthday: '11.12.1996'}, 
               {name: 'Eric' , birthday: '12.12.1989'}, 
               {name: 'Mark' , birthday: '5.01.1993'}]
var friendsBirthDays = friends.map(function(friend){
    return moment(friend.birthday, 'DD.MM.YYYY');
});
moment.max(friendsBirthDays).format('DD.MM.YYYY'); // 11.12.1996
```

## 查詢

isBefore 是用來查詢是否在早於後面的時間

```javascript
moment('2010-10-20').isBefore('2010-10-21') // true
moment('2010-10-20').isBefore('2010-12-31', 'year') // false
```

isSame 是用來查詢是否和後面的時間相等

```javascript
moment('2010-10-20').isSame('2009-12-31', 'year') // false
moment('2010-10-20').isSame('2010-01-01', 'year') // true
```

isAfter 是用來查詢是否和晚於後面的時間

```javascript
moment('2010-10-20').isAfter('2010-10-19') // true
moment('2010-10-20').isAfter('2010-01-01', 'year') // false
```

isSame 是用來查詢是否在設定的時間範圍內

```javascript
moment('2010-10-20').isBetween('2010-10-19', '2010-10-25') // true
moment('2010-10-20').isBetween('2010-01-01', '2012-01-01', 'year') // false
```

## 更換語言

預設為英文，如果要更改為中文顯示可以先定義切換的 locale 模式

moment.locale\(\);  
\(\)為空預設為英文

```javascript
moment.locale('zh-tw'); 
moment().format('LLLL'); // 2018年11月7日星期三下午2點25分
```

