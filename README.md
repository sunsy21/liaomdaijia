<!DOCTYPE html>
<html lang="zh-CN">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>辽M代驾价格查询</title>
<style>
  * {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
  }
  body {
    font-family: "Microsoft YaHei", sans-serif;
    background: #f0f8ff;
    padding-bottom: 30px;
  }
  .header {
    background: #1976d2;
    color: white;
    text-align: center;
    padding: 16px;
    font-size: 18px;
    font-weight: bold;
  }
  .container {
    padding: 20px;
  }
  #searchInput {
    width: 100%;
    padding: 16px;
    font-size: 18px;
    border: 1px solid #ccc;
    border-radius: 8px;
    margin-bottom: 16px;
    outline: none;
  }
  .searchBtn {
    width: 100%;
    height: 55px;
    background: #1976d2;
    color: white;
    border: none;
    border-radius: 8px;
    font-size: 20px;
    font-weight: bold;
    margin-bottom: 20px;
    cursor: pointer;
  }
  .tip {
    background: #fff3cd;
    padding: 12px;
    border-radius: 8px;
    font-size: 16px;
    margin-bottom: 20px;
  }
  .title {
    font-size: 18px;
    font-weight: bold;
    margin: 10px 0;
  }
  .item {
    background: white;
    padding: 16px;
    border-radius: 8px;
    border: 1px solid #bbdefb;
    margin-bottom: 6px;
    display: flex;
    justify-content: space-between;
    font-size: 20px;
  }
  .price {
    color: red;
    font-weight: bold;
    font-size: 22px;
  }
  .empty {
    text-align: center;
    color: #888;
    font-size: 18px;
    padding: 20px 0;
  }
  .footer {
    text-align: center;
    margin-top: 30px;
  }
  .footer1 {
    font-size: 18px;
    color: #666;
    margin-bottom: 10px;
  }
  .footer2 {
    font-size: 17px;
    color: #1976d2;
    font-weight: bold;
    margin-bottom: 6px;
  }
  .footer3 {
    font-size: 15px;
    color: #555;
  }
</style>
</head>

<body>

<div class="header">辽M代驾价格查询-孙露制作</div>

<div class="container">
  <input type="text" id="searchInput" placeholder="请输入地址">
  <button class="searchBtn" onclick="search()">查 询</button>

  <div class="tip">
    注：晚 10:30 后长途订单给公司打电话定价格!不允许司机自己私自谈价加钱，若客户投诉直接与公司解除合作关系。
  </div>

  <div id="resultArea"></div>

  <div class="footer">
    <div class="footer1">服务时间：上午10:00 — 凌晨02:00</div>
    <div class="footer2">辽M代驾.统一报价.安全可靠</div>
    <div class="footer3">软件内容更新修改价格，请联系孙露，电话18742208808</div>
  </div>
</div>

<script>
  // 新区价格
  const newAreaPrices = {
    "新区往返": 50,
    "物流城": 20,
    "阮家": 20,
    "红光村": 25,
    "大莲花": 30,
    "五角湖": 30,
    "小莲花": 30,
    "江河泡": 30,
    "新兴堡": 30,
    "牛岗子": 30,
    "辽海屯": 30,
    "园林雅居": 30,
    "英城子": 30,
    "西站": 30,
    "左家沟": 35,
    "七里屯": 35,
    "水上乐园": 35,
    "农校": 35,
    "范家屯": 40,
    "沙山子": 40,
    "雅居山庄": 30,
    "边家": 40,
    "贺家": 30,
    "老官台": 50,
    "乡村爱情基地": 40,
    "地运所": 40,
    "柴河沿": 50,
    "养马堡": 40,
    "灵宝寺": 40,
    "熊官屯": 40,
    "三台子": 50,
    "腰堡": 50,
    "何家山庄": 40,
    "黄金沟": 50,
    "高强": 50,
    "树芽屯": 50,
    "八宝岭": 40,
    "建设村": 50,
    "椴木岭": 50,
    "河夹心": 50,
    "小白梨": 50,
    "张楼子": 60,
    "梨花山庄": 60,
    "平顶堡": 60,
    "双井子": 80,
    "镇西堡": 60,
    "新台子": 60,
    "大白梨": 70,
    "上欲村": 80,
    "山头堡": 70,
    "蔡牛村": 80,
    "阿吉": 80,
    "下欲村": 70,
    "调兵山": 100,
    "开原": 100,
    "大甸子": 100,
    "清河": 120,
    "靠山屯": 120,
    "大明小明": 120,
    "法库": 160,
    "沈阳": 200,
    "抚顺": 200,
    "昌图": 200,
    "英守屯": 40,
    "城南堡": 30,
    "金峰小镇": 30,
  };

  // 老区价格
  const oldAreaPrices = {
    "老区往返": 50,
    "英城子": 20,
    "七里屯": 25,
    "左家沟": 25,
    "农校": 25,
    "水上乐园": 25,
    "物流城": 30,
    "小莲花": 30,
    "江河泡": 30,
    "新兴堡": 30,
    "牛岗子": 30,
    "辽海屯": 30,
    "五角湖": 30,
    "大莲花": 30,
    "阮家": 30,
    "红光村": 30,
    "园林雅居": 30,
    "地运所": 30,
    "柴河沿": 30,
    "三台子": 35,
    "乡村爱情基地": 30,
    "养马堡": 30,
    "熊官屯": 30,
    "灵宝寺": 35,
    "英守屯": 50,
    "沙山子": 40,
    "雅居山庄": 30,
    "老官台": 40,
    "八宝岭": 30,
    "建设村": 40,
    "何家山庄": 30,
    "范家屯": 50,
    "边家": 50,
    "贺家": 40,
    "镇西堡": 50,
    "张楼子": 50,
    "平顶堡": 50,
    "高强": 50,
    "树芽屯": 40,
    "椴木岭": 50,
    "小白梨": 40,
    "城南堡": 30,
    "西站": 40,
    "梨花山庄": 50,
    "黄金沟": 40,
    "大白梨": 60,
    "腰堡": 60,
    "抚顺": 200,
    "大明小明": 120,
    "山头堡": 60,
    "新台子": 70,
    "法库": 160,
    "清河": 120,
    "李千户": 70,
    "崔镇堡": 70,
    "蔡牛村": 90,
    "阿吉": 90,
    "靠山屯": 100,
    "调兵山": 100,
    "开原": 100,
    "大甸子": 100,
    "沈阳": 200,
    "昌图": 200,
    "金峰小镇": 40,
  };

  function search() {
    let keyword = document.getElementById("searchInput").value.trim();
    let area = document.getElementById("resultArea");
    area.innerHTML = "";

    if (!keyword) {
      area.innerHTML = '<div class="empty">请输入地址</div>';
      return;
    }

    // 查找匹配
    让 旧列表 = 查找匹配(旧区域价格，关键字);
    让 新列表 = 查找匹配(新价格，关键字);

    让 超文本标记语言 = "";

    如果 (旧列表。长度 > 0) {
html +=< div class="title " >老区价格</div > ';
旧列表。为每一个(项目 => {
html +=`
          <div class="item">
            <span>老区到 ${项目。名字}</span>
            <span class="price">${项目。价格}元</span >
          </div>
        `;
      });
    }

    如果 (新名单。长度 > 0) {
html +=< div class="title " >新区价格</div > ';
新名单。为每一个(项目 => {
html +=`
          <div class="item">
            <span>新区到 ${项目。名字}</span>
            <span class="price">${项目。价格}元</span >
          </div>
        `;
      });
    }

    如果 (html ==="") {
html =< div class="empty " >未找到相关地址,请联系公司确认</div > ';
    }

面积。innerHTML= html
  }

  功能 查找匹配(mapData, 关键字) {
    让 目录 = [];
    为 (让 名字 在mapData) {
      如果 (姓名。包含(关键字)) {
列表。推({ 名字:名称，价格:mapData[名字] });
      }
    }
    返回列表；
  }
</脚本>

</身体>
</超文本标记语言>
