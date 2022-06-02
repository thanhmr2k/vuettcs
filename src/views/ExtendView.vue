<template>
    <div class="intro">
        <h2>Đặng Đình Thành - B19DCCN648</h2>
        <h1>Mô tả</h1>
        <p>Đây là web em xây dựng để cập nhật thông tin thời tiết và dự báo thời tiết trong 7 ngày với tên thành phố nhập vào, có phần map với graph</p>
        <h1>Tính năng</h1>
        <p>Khi nhập tên thành phố/ địa điểm vào thanh tìm kiếm và bấm enter, data tên thành phố dạng text nhập vào được đưa vào hàm js fetchWeather để xử lý. 
            API em sử dụng là https://weatherdbi.herokuapp.com/data/weather/{địa điểm}.
            API này cung cấp data lẫn hình ảnh để biểu diễn trên thanh chart và weather-wrap</p>
        <h1>Công nghệ</h1>
        <p>Project làm từ Vue.js, cụ thể ứng dụng các công nghệ như sau:</p>
        <ul class="a">
            <li>vue-chart.js</li>
            <li>vue-animation</li>
            <li>vue-CLI</li>
            <li>Vue single file component</li>
            <li>Vue route</li>
        </ul>
    </div>
</template>
<script>

export default {
    name: 'App',
}
</script>
<style scope>
*{
    margin: 0;
    padding: 0;
    color:aliceblue;
}
.intro{
    text-align: left;
    padding-left: 20px;
    height: 100vh;
    background-image: linear-gradient(to bottom, rgba(102, 126, 234, 1), rgba(118, 75, 162, 1));
}
ul.a {
  list-style-type: circle;
}
</style>