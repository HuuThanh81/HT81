---
weight: 4
title: "Array - Trắc nghiệm tính cách"
date: 2020-10-15T21:57:40+08:00
lastmod: 2020-01-01T16:45:40+08:00
draft: false
author: "Hữu Thành"
authorLink: "https://www.facebook.com/OGCN01"
description: "This article shows the basic Markdown syntax and format."
resources:
- name: "featured-image"
  src: "featured-image.png"

tags: ["Question", "PHP", "Array"]
categories: ["PHP Programming - Basics"]

lightgallery: true
---

Trắc nghiệm tính cách với php.

<!--more-->

### 1. Viết chương trình “Trắc nghiệm tích cách” với giao diện như sau:

### Yêu cầu chức năng:
    - Hiển thị các câu hỏi và các lựa chọn trả lời cho mỗi câu hỏi (dạng nút radio).
    - Sau khi người dùng đã trả lời hết các câu hỏi, bấm nút “Kiểm tra”, thì xuất kết quả ra màn hình.


### Tổ chức dữ liệu:
    - Danh sách câu hỏi, file question.txt
        id|question
        01|Bạn cảm thấy dễ chịu nhất khi nào?
        02|Bạn thường bước đi:
        03|Khi nói chuyện với người khác, bạn:
        04|Khi nghỉ ngơi, bạn ngồi như thế nào?
        05|Khi ngạc nhiên thích thú, bạn phản ứng thế nào?
        06|Khi đi dự tiệc, bạn:
        07|Bạn đang làm việc và tập trung cao độ thì bị cắt ngang. Bạn sẽ:
        08|Bạn thích màu nào nhất trong các màu dưới đây?
        09|Khi đi ngủ, lúc sắp ngủ, bạn nằm trong tư thế nào?
        10|Bạn thường mơ mình:


    - Phương án trả lời, file options.txt
        question_id|option_id|option|point
        01|a|Vào buổi sáng|2
        01|b|Vào buổi chiều và chớm tối|4
        01|c|Vào đêm muộn|6
        02|a|Khá nhanh với bước chân dài|6
        02|b|Khá nhanh với bước chân ngắn|4
        02|c|Không nhanh lắm, đầu ngẩng cao, hướng mặt ra cả thế giới|7
        02|d|Không nhanh lắm, đầu cúi xuống|2
        02|e|Rất chậm|1
        03|a|Đứng, khoanh tay|4
        03|b|Siết chặt hai bàn tay|2
        03|c|Đặt một hoặc cả hai tay lên hông|5
        03|d|Chạm hoặc đẩy người đối thoại|7
        03|e|Sờ tai, xoa cằm hoặc nghịch tóc|6
        04|a|Đầu gối cong, hai chân khép sát vào nhau|4
        04|b|Hai chân bắt chéo nhau|6
        04|c|Hai chân duỗi thẳng|2
        04|d|Khoanh chân|1
        05|a|Cười lớn|6
        05|b|Cười, nhưng không cười lớn|4
        05|c|Cười lặng lẽ|3
        05|d|Cười bẽn lẽn, ngượng ngùng|5
        06|a|Gây ồn ào khi đến để mọi người chú ý|6
        06|b|Đến lặng lẽ, và tìm người bạn quen biết|4
        06|c|Bước vào một cách lặng lẽ nhất, cố gắng không bị chú ý|2
        07|a|Chào đón "kẻ phá đám"|6
        07|b|Cảm thấy thực sự khó chịu|2
        07|c|Mơ hồ giữa hai thái cực|4
        08|a|Đỏ hoặc cam|6
        08|b|Đen|7
        08|c|Vàng hoặc xanh nhạt|5
        08|d|Xanh lá cây|4
        08|e|Xanh đậm hoặc tím|3
        08|f|Trắng|2
        08|g|Nâu hoặc xám|1
        09|a|Nằm ngửa duỗi thẳng|7
        09|b|Nằm úp, duỗi thẳng|6
        09|c|Nằm nghiêng về một bên, hơi co|4
        09|d|Tay gối đầu|2
        09|e|Chùm đầu|1
        10|a|Rớt|4
        10|b|Đánh đấm hoặc vật lộn|2
        10|c|Tìm kiếm một vật gì hoặc người nào|3
        10|d|Bay hoặc trôi|5
        10|e|Ít khi mơ|6
        10|f|Giấc mơ của bạn luôn vui vẻ dễ thương|1


    - Kết quả, file result.txt
        min|max|result


        0|20|Mọi người nghĩ bạn là người nhút nhát, hay run sợ, và thiếu quyết đoán, bạn là người luôn cần sự quan tâm, và luôn luôn muốn một ai đó khác đưa ra quyết định cho mình và chẳng bao giờ muốn tham gia bất cứ điều gì với bất cứ ai! Mọi người coi bạn là người hay lo lắng vào những vấn đề không tồn tại. Một số người nghĩ rằng bạn là người nhàm chán nhưng chỉ những người thật sự hiểu bạn mới biết rằng bạn không phải như thế.


        21|30|Bạn bè của bạn coi bạn là người chịu khó và kén chọn. Họ coi bạn là người rất thận trọng, vô cùng cẩn thận, chậm và ổn định̀. Sẽ thật sự rất ngạc nhiên nếu bỗng nhiên bạn làm điều gì đó bốc đồng hay hấp tấp . Bạn là người có thể kiểm tra và suy xét tất cả mọi thứ một cách cẩn thận từ mọi góc độ và sau đó quyết định của bạn có thể đi ngược lại nó. Mọi người nghĩ rằng những phản ứng này là do một phần trong tính cách thận trọng của bạn.


        31|40|Mọi người cảm thấy bạn nhạy cảm, thận trọng, kỹ lưỡng và thực tế. Họ coi bạn là người thông minh, tài năng và khiêm tốn. Bạn không kết bạn quá nhanh hoặc quá dễ dàng, nhưng bạn cực kỳ trung thành với bạn bè và cũng mong đợi từ bạn của mình một lòng trung thành trở lại. Những người bạn thật sự của bạn luôn biết rằng phải rất khó khăn mới có thể làm bạn mất đi sự tin tưởng ở bạn bè của bạn, nhưng việc đó cũng đồng nghĩa rằng một khi lòng tin tưởng đó đổ vỡ thì cũng khó mà hàn gắn.


        41|50|Mọi người thấy bạn tươi mát, sinh động, vui vẻ, thiết thực, và luôn luôn thú vị. Bạn luôn là trung tâm của sự chú ý, nhưng vừa đủ cân bằng chứ không để cho nó vượt qua giới hạn. Mọi người thấy bạn là người tử tế, ân cần, một người hiểu biết và sẽ luôn luôn cổ vũ và giúp đỡ họ.


        51|60|Mọi người coi bạn là một người thú vị, hay thay đổi, tánh tình bốc đồng; bạn được sinh ra để là một nhà lãnh đạo. Bạn là người quyết định mọi việc nhanh chóng, mặc dù không phải lúc nào những quyết định đó cũng chính xác. Mọi người coi bạn là một người táo bạo và mạo hiểm, và sẽ cố gắng thử thách bất cứ điều gì đó một lần. Bạn là người biết nắm bắt cơ hội và thích thú những cuộc phiêu lưu. Mọi người thích được ở bên bạn bởi vì những sự hứng thú mà bạn đem đến cho họ.


        61|200|Bạn là người mà người khác cảm thấy cần phải đề phòng. Họ thấy bạn là người hão huyền và thích được làm trung tâm của mọi sự chú ý. Cá tính của bạn cũng rất trội và mạnh mẽ. Mọi người có thể khâm phục bạn và mong muốn được như bạn, nhưng họ lại không tin tưởng bạn và luôn ngần ngại, không muốn quá dính líu với bạn.

### DEMO

>App source Repl.it : https://repl.it/@HuuThanh81/Ex-Array#result.txt

{{< iframe src="https://ex-array.huuthanh81.repl.co/?lite=true" >}}