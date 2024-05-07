
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Social Data Analysis</title>
    <style>
        .header-image {
            width: 100%;
            height: auto;
        }
    </style>
</head>
<body>
    <!-- 确保src路径指向正确的图片位置 -->
    <img src="/assets/1.png" alt="Social data analysis and visualization Spring '24" class="header-image">
</body>
</html>




Then we divided individuals into two groups based on their mode of transportation: those who travel by car and those who use other transportation modes. An interactive plot was then created to examine differences in fare type, travel purpose, and the days of the week people travel.
<iframe src="/assets/interactive_plot.html"
    sandbox="allow-same-origin allow-scripts"
    width="100%"
    height="500"
    scrolling="no"
    seamless="seamless"
    frameborder="0">
</iframe>
Based on the interactive comparison plot, here we can see:

Fare Type: The majority of travelers either pay full fare or travel for free. There are consistently more travelers in each category who choose other modes over traveling by car. Notably, there is a higher proportion of disabled individuals opting for modes other than cars.

Travel Purpose: A significant number of people travel for Home-Based Other (HBO) purposes. In every category, the number of individuals using modes other than cars exceeds those who travel by car.

Day of the Week: Car users typically travel on weekends, with fewer choosing to travel on Mondays. Conversely, those who use other modes prefer to travel on weekdays, particularly on Fridays.
