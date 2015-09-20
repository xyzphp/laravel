laravel blade模板引擎学习
================================
1.定义一个页面布局模板

>定义一个视图片断

>>		@section('sidebar')

>>			This is the master sidebar.

>>		@show

>展示某个指定 section 所代表的内容

>>		@yield('title')

2.扩展一个页面布局模板

>为子页面指定其所“继承”的页面布局模板

>>		@extends('layouts.master')

>重载父类模板的定义的 section 的内容

>>		@section('title', 'Page Title')

>重载父类模板的定义的视图片段

>>		@section('sidebar')

>>			@parent #继承父类模板定义视图片段的内容

>>			<p>This is appended to the master sidebar.</p>

>>		@endsection

		