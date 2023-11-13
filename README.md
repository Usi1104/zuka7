# zuka7
# 演習１
``` mermaid
sequenceDiagram
actor a as 医者
actor b as 学生
actor c as 教員
actor d as データベース

b->>a:診断書の発行を依頼
a-->>b:診断書を発行・受け渡し

loop影響が出そうな    教員全員に
b->>c:診断書を提出
c->>+d:病欠を登録＜依頼＞
d-->>-c:病欠を登録＜完了＞
end
```
# 演習２
``` mermaid
sequenceDiagram
actor a as 医者
actor b as 学生
actor c as 教員
actor d as データベース
actor e as 事務局

b->>a:診断書の発行を依頼
a-->>b:診断書を発行・受け渡し
b->>e:診断書を事務局に提出
loop影響が出そうな教員全員に
e->>c:診断書を提出
c->>+d:病欠を登録＜依頼＞
d-->>-c:病欠を登録＜完了＞
end
```
# 演習３
``` mermaid
sequenceDiagram
actor a as 医者
actor b as 学生
actor c as 教員
actor d as データベース
actor e as 事務局
alt 病院にかかった場合
b->>a:診断書の発行を依頼
a-->>b:診断書を発行・受け渡し
b->>e:診断書を提出
else 発熱があった場合
b->>e:発熱報告書を提出
end
e-->>b:確認書を発行
loop 影響が出そうな    教員全員に
b->>c:確認書を提出
opt 病欠を認める場合
c->>+d:病欠を登録＜依頼＞
d-->>-c:病欠を登録＜完了＞
end
end
```
# 課題
``` mermaid
sequenceDiagram
actor a as 医者
actor b as 学生
actor c as 教員
actor d as データベース
actor e as 事務局
alt 病院にかかった場合
b->>a:診断書の発行を依頼
a-->>b:診断書を発行・受け渡し
b->>e:診断書を提出
else 発熱があった場合
b->>e:発熱報告書を提出
end
e-->>b:病欠の可否を通知する
opt 病欠可の場合
e->>d:病欠を登録
end
loop 該当の（病欠期間内）    教員全員に
d->>c:配慮願いメールを送信
end
```
