---
title:      "ウェブインターフェースを備えた見守りカメラを作る"
date:       2016-06-21 09:00:00 +0900
categories: Make
tags:       DIY RaspberryPi
---

<a href="https://0x0026.info/">Home</a>

## ウェブインターフェースを備えた見守りカメラの制作

### 概要

#### ニーズ
* 「動体検知ができてメール通知のできる低コストに導入可能な見守りカメラ」
  * 近隣で空き巣が起きており、玄関や勝手口付近を監視したい
  * 認知症の初期症状がある一人暮らし家族の見守りをしたい
  * 初期コストおよび運用コストの低いこと
  * カメラの台数を柔軟に増やせること

#### とりあえず作ってみる
* 動体検知機能を組み込んだ見守りカメラのシステムを構築
  * 監視カメラのオープンソースソフトウェアを利用し、Raspberry Piに組み込む
  * 通信を柔軟に制御できるIoTに最適化された通信回線であるSoracom Airを利用する

### 構成
* Raspberry Pi 2 Model B
  * Wi-Fiを搭載したRaspberry Pi 3 Model B や 小型の Raspberry Pi Zero W でも可

* 監視用ソフトウェア
  * ![motionEye](https://github.com/ccrisan/motioneye) または ![motionEyeOS](https://github.com/ccrisan/motioneyeos)
  * カメラモジュール、WebカメラやIPカメラを接続することができる
  * 動体検知エリアの設定、メールの通知先、画像の保存容量などをWebUIから設定できる
 
* Webカメラ
  * 既製品のUSB接続またはIPカメラ
  * 30万画素〜100万画素がスムーズに動く

* USBメモリー（必要に応じて）
  * システムが格納されたSDカードと画像を保存するUSBメモリーを分けることで、交換等の運用が容易になる
  * 16GBあれば屋内・屋外の動体検知を2ヶ月くらい保存できる
  * motionEyeOSが認識できるよう、FATまたはFAT32でフォーマットしておく

* ngrok（必要に応じて）
  * トンネリングサービス。固定IPアドレスを持たない契約や、モバイルルーター越しでもWebUIへのアクセスが可能になる
  * 設定変更を現地に行かなくてもWeb上で行うことができる

###  結果
![](/assets/2016-06-21/1.jpg))

3世帯に5箇所のウェブ見守りカメラを導入済み、切断などのトラブルなく概ね好評。  
今回可能になったことは以下の通り。

* IoT向けの通信回線を用いることで、固定回線のない家庭にも低コストで導入できる
* 撮影した画像をメール通知またはクラウドから閲覧できる
* 既製品のWebカメラやIPカメラを柔軟に組み合わせることができる

---

<h4>記事一覧</h4>

<h4>新着</h4>

<ul>
    {% for post in site.posts limit:3 %}
        <li>
            <a href="{{ post.url }}">{{ post.title }}</a>
        </li>
    {% endfor %}
</ul>

<h4>カテゴリー</h4>

{% for category in site.categories %}
  {% capture name %}{{ category[0] }}{% endcapture %}
  <h5>{{ name }} ({{ site.categories[name] | size }})</h5>
  <ul class="posts">
  {% for post in site.categories[name] limit:3 %}
    <li>
      <a class="post-link" href="{{ post.url | prepend: site.baseurl }}">{{ post.title }}</a>
      <span class="post-date">{{ post.date | date_to_string }}</span>
    </li>
  {% endfor %}
  </ul>
{% endfor %}

<h4>タグ</h4>

{% for tag in site.tags %}
  {% capture name %}{{ tag[0] }}{% endcapture %}
  <h5>{{ name }} ({{ site.tags[name] | size }})</h5>
  <ul class="posts">
  {% for post in site.tags[name] %}
    <li>
      <a class="post-link" href="{{ post.url | prepend: site.baseurl }}">{{ post.title }}</a>
      <span class="post-date">{{ post.date | date_to_string }}</span>
    </li>
  {% endfor %}
  </ul>
{% endfor %}
