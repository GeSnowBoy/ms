## 说明

```javascript
在index.js文件实现函数
function translateArrayToTree(list) {
}
将下面数据
[
  { name: "男士奢侈品T恤", parentId: "agicy4zcr9c0", id: "agid00hlgpvk", weight: 10, },
  { name: "男士奢侈品", parentId: "agicwn8nwg00", id: "agicy4zcr9c0", weight: 7, },
  { name: "奢侈品", parentId: "ROOT", id: "agicwn8nwg00", weight: 4 },
  { name: "男士卡通T恤", parentId: "agic2j6la77k", id: "agic44o9nh8g", weight: 2, },
  { name: "男士T恤", parentId: "agic1fc13lds", id: "agic2j6la77k", weight: 1 },
  { name: "T恤", parentId: "ROOT", id: "agic1fc13lds", weight: 11 },
  { name: "女士系列", parentId: "aetri28cdt44", id: "af42gq1xe0ow", weight: 15, },
  { name: "x c v c v", parentId: "ROOT", id: "aetri28cdt44", weight: 0 },
]
转换成
[
  {
    name: "ROOT",
    id: "ROOT",
    children: [ {
        name: "x c v c v",
        id: "aetri28cdt44",
        children: [{ name: "女士系列", id: "af42gq1xe0ow", children: [] }],
      }, {
        name: "奢侈品",
        id: "agicwn8nwg00",
          children: [{
              name: "男士奢侈品", id: "agicy4zcr9c0",
              children: [{ name: "男士奢侈品T恤", id: "agid00hlgpvk", children: [] },],
          },],
      }, {
        name: "T恤",
        id: "agic1fc13lds",
        children: [ {
            name: "男士T恤", id: "agic2j6la77k",
            children: [ { name: "男士卡通T恤", id: "agic44o9nh8g", children: [] }, ],
          }, ],
      }, ],
  },
];
```
## 注意事项
*  数据需要按照 `weigth` 字段排序
*  根元素`id`为`ROOT`,需自己生成
*  运行 `node index.js` 可查看运行结果

## 附录
```typescript
原数据格式
interface Data1 {
    name:     string; // 分类名称
    parentId: string; // 父分类ID
    id:       string; // 分类ID
    weight:   number; // 权重 数值越小权重越大
}
转换后数据格式 (Data2[])
interface Data2 {
    name:     string; // 分类名称
    id:       string; // 分类ID
    children: Data2[];// 子分类列表
}
```
