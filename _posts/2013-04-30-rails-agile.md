---
layout: post
title: "つまずいた箇所メモ『RailsによるアジャイルWebアプリケーション開発 第4版』"
imagefeature: 
featured: true
description: "Its ON, baby"
headline: "Let's Fire up the Engines"
categories: [Trouble shooting]
tags:
  - Ruby
  - Rails
---
<h3>Rails 3.2.13</h3>

<h4>P107</h4>
<a href="http://banker0507.blogspot.jp/2012/06/rails323cant-mass-assign-protected.html">Rails3.2.3でCan't mass-assign protected attributes: productと出る。</a>

<h4>P108</h4>
<a href="http://masakazy.hatenablog.com/entry/2013/04/05/040507">RailsによるアジャイルWebアプリケーション開発P108でundefined method `title' for nil:NilClass エラーにつまづく。 - リバーシブルが良い!</a>

<h4>P152</h4>
<blockquote>ActiveModel::MassAssignmentSecurity::Error in OrdersController#create
Can't mass-assign protected attributes: name, address, email, pay_type</blockquote>
 
<pre class="lang:ruby decode:true " title="depot/app/models/order.rb" ># encoding: utf-8
class Order &lt; ActiveRecord::Base
  attr_accessible :name, :address, :email, :pay_type
  PAYMENT_TYPES = [ "現金", "クレジットカード", "注文書" ]</pre> 

attr_accessible の記述が必要。


<h4>P182</h4>
<blockquote>Gem::LoadError (bcrypt-ruby is not part of the bundle. Add it to Gemfile.):</blockquote>
<a href="http://ameblo.jp/daikichi-linux/entry-11128393923.html">rails エラー対処(1)｜だいきちのブログ</a>
Gemfileに gem 'bcrypt-ruby' を追記して bundle install 。
