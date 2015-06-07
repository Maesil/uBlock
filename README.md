[<img src="https://travis-ci.org/gorhill/uBlock.svg?branch=master" height="18">](https://travis-ci.org/gorhill/uBlock)
[![Crowdin](https://d322cqt584bo4o.cloudfront.net/ublock/localized.png)](https://crowdin.com/project/ublock)

***

**0.9.8.2 버전의 크로미움이 새 권한을 요구하는것에 대하여**: [필요한 권한들에 대해: 개인 정보 보호 관련 설정을 변경한다](https://github.com/gorhill/uBlock/wiki/About-the-required-permissions#change-your-privacy-related-settings).크롬 웹 스토어에서 누군가의 지적으로 생긴 부정적인 리뷰에 대한 개발자의 답변:

> 이 변경 이후 부정적인 리뷰가 생긴것은 주목할 가치가 있다

저는 이 긴 프로젝트를 보았습니다. 제 결정은 장기적 기간 후에 입증됩니다. 어떤 일이 일어났는지 완전히 이해하지 않은 상태로 그저 무릎을 꿇리게 하려는 사람들의 행동은 제가 개인정보 보호 습관을 약화시킨다고 하는 것에 대해서는 좋은 이유가 아닙니다. 당신이 원한다면 다음 버전에서 다시 활성화 되게 할 것입니다만, 모든 이유에 의해 프리-페칭 기능은 기본적으로 비활성화되게 할 것입니다. 제 목표는 사용자가 관심을 가지는 데이터를 캐내고 사용자의 이익을 손상시키는 '데이터 광부' 등의 행동이 아닙니다. 사용자의 프리-페칭을 비활성화하는 것은 이와 같은 것이 됩니다.

**두 개의 루머에 대한 답변**: 최근 많은 곳에서 다음과 같은 주장을 보았습니다 ([예시1](https://np.reddit.com/r/AskReddit/comments/35s2je/whats_a_product_that_everybody_uses_but_nobody/cr7h8l6), [예시2](https://np.reddit.com/r/leagueoflegends/comments/37e8ed/want_to_support_your_favorite_content_producers/)):

> 단지 uBlock은 애드블록 플러스처럼 광고를 차단한다. 그러나 광고 API에게는 광고를 본 것처럼 트리거한다.

**완전히 거짓입니다.** uBlock Origin (및 uBlock)은 어떤 "광고 API" 든지 "트리거" 하지 않습니다(어떤 것이든). 그것은 필터 목록에 따라 만들어지는 네트워크 요청을 방지합니다. 그러므로 당신의 브라우저는 원격 서버에 연결되지 않습니다. 언제든.

**uBlock의 목적은 오직 사용자의 이익이며, 다른 것에는 관여하지 않습니다**. [uBlock 선언서](https://github.com/gorhill/uBlock/blob/master/MANIFESTO.md)를 참조하세요..

*** 

<h1 align="center">
<sub>
<img  src="https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/icon38@2x.png"
      height="38"
      width="38">
</sub>
uBlock Origin
</h1>
<p align="center">
<sup> <!-- Pronounciation -->
        <i>유-블록 오리진</i> 이라고 부릅니다(<code>/ˈjuːˌblɒk/</code>) — <i>당신</i>이 원하는대로 브라우저에 입력하세요.
</sup>
<br>
<sup> <!-- Languages -->
      <img src="https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/languageicon-36.png" width="18" height="18">
      <sup>
            <a href="https://github.com/gorhill/uBlock/">
            English,          <a href="https://github.com/fang5566/uBlock/blob/master/README.md#-µblock">
            Chinese (中文),   </a><a href="https://github.com/delightbot/uBlock/blob/master/README.md#ublock">
            Korean (한국어)   </a>
      </sup>
</sup>
</p>


**여러 브라우저를 위한 빠르고, 강력하고, 효율적인 차단기입니다.**&nbsp;&nbsp;[<img src="https://travis-ci.org/gorhill/uBlock.svg?branch=master" height="12">](https://travis-ci.org/gorhill/uBlock)

* [용도 및 정보](#서론)
* [설명서](#설명서)
* [성능 및 효율성](#성능 및 효율성)
  * [메모리](#메모리)
  * [CPU](#CPU)
  * [차단 기능](#차단)
  * [빠른 테스트](#빠른 테스트)
* [설치](#설치)
  * [크로미움](#크로미움)
  * [파이어폭스](#파이어폭스)
  * [사파리](#사파리)
* [릴리즈 내역](#릴리즈 내역)
* [위키](https://github.com/gorhill/uBlock/wiki)

## 서론

uBlock Origin (또는 uBlock₀) 은 단순히 *광고 차단기*가 아닙니다; 여러가지 부분에서 쓸 수 있는 범용 차단기입니다. uBlock₀은 [애드블록 플러스 필터 구문](https://adblockplus.org/en/filters)를 통해 광고를 차단합니다. uBlock₀은 구문을 [확장](https://github.com/gorhill/uBlock/wiki/Filter-syntax-extensions)하고 사용자 정의 규칙 및 필터 사용이 가능하도록 설계되었습니다.

상기해두세요, 이 차단기를 사용하는 것은 **절대** [도둑질](https://twitter.com/LeaVerou/status/518154828166725632)이 아닙니다. 이런 오싹한 상상에 빠지지 마세요. _궁극적_인 논리의 결과가 `차단 = 도둑질` 이라면 이는 불가침적인 개인정보 권리에 대한 범죄입니다.

광고들, "거슬리지 않거나" 혹은 아닐뿐이지만, 요즘 당신이 방문하는 사이트에서 광고가 보이는 부분은 그저 개인정보를 알아내려는 장치의 눈에 보이는 부분일 뿐입니다. **uBlock₀의 주 목표는 사용자가 개인정보 침해 장치를 무력화시키는 것을 돕는 것입니다.** — 이러한 사용자들을 환영하는 방식으로 더 많은 기술을 원하지 않는 사용자들을 위해, 참여 방법을 마련했습니다. (예를 들어, [µMatrix](https://github.com/gorhill/uMatrix) 같은 것들).

_EasyList_, _Peter Lowe's Adservers_, _EasyPrivacy_ 와 _Malware domains_ 는 uBlock₀을 설치할 때 기본적으로 활성화 되어 있습니다. 다른 많은 블록 트래커, 분석 등을 쉽게 사용할 수 있습니다. 호스트 파일도 지원됩니다.

uBlock₀을 설치하고, 당신이 생각하기에 uBlock₀의 차단목록이 너무 많다고 생각되면 쉽게 필터 리스트에서 선택 해제가 가능합니다. 참고로, 애드블록 플러스는 설치시 _EasyList_ 만 기본적으로 활성화되어 있습니다.

## 설명서

[빠른 가이드: 팝업 유저 인터페이스](https://github.com/gorhill/uBlock/wiki/Quick-guide:-popup-user-interface)

<a href="https://github.com/gorhill/uBlock/wiki/Quick-guide:-popup-user-interface"><img src="https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/popup-1.png" /></a>

고급 사용자분들은, [유동 필터링](https://github.com/gorhill/uBlock/wiki/Dynamic-filtering:-quick-guide)과 [uBlock₀ 위키](https://github.com/gorhill/uBlock/wiki)를 참조하세요.

## 성능

#### 메모리

<div align="center">
다음 벤치마크를 평균적으로 따져보면, uBlock₀은 당신의 브라우저를 훨씬 더 가볍게 만듭니다. <sup>[1]</sup><br><br>

크로미움 <sup>[2]</sup><br>
<img src="https://raw.githubusercontent.com/gorhill/uBlock/master/doc/benchmarks/mem-usage-overall-chart-20141224.png" /><br><br>

파이어폭스<br>
<img src="https://raw.githubusercontent.com/gorhill/uBlock/master/doc/benchmarks/mem-usage-overall-chart-20150205.png" /><br><br>

사파리<br>
<img src="https://raw.githubusercontent.com/gorhill/uBlock/master/doc/benchmarks/mem-usage-overall-chart-safari-20150205.png" /><br><br>

</div>

<sup>[1] 자세한 메모리 사용량에 대한 벤치마크를 <a href="https://github.com/gorhill/uBlock/wiki/Firefox-version:-benchmarking-memory-footprint">파이어폭스 버전: 메모리 사용량 벤치마크</a> 에서 확인이 가능합니다.</sup><br>

<sup>[2] 중요한 사항: 현재 여기에는 [크로미움 39+ 기반에서 부가 기능이 열려 팝업 UI이 뜰 때마다 메모리 릭이 발생하는 버그](https://code.google.com/p/chromium/issues/detail?id=441500)가 존재합니다. 이것은 <i>모든</i> 부가 기능에 영향을 줍니다. 크로미움 기반에서 메모리 사용량을 측정할 때 이 점을 유의해 주십시오. 벤치마크에서, 저는 완전하게 팝업을 여는 것을 피했습니다.</sup><br>

#### CPU

<p align="center">
uBlock₀은 CPU에 부담이 적습니다.<br>
<img src="https://raw.githubusercontent.com/gorhill/uBlock/master/doc/benchmarks/cpu-usage-overall-chart-20141226.png" /><br>
<sup>자세한 벤치마크를 이 <a href="https://github.com/gorhill/uBlock/blob/master/doc/benchmarks/cpu-usage-overall-20141226.ods">리브레오피스 스프레드시트</a>에서 확인이 가능합니다.</sup>
</p>

#### 차단

<p align="center">
매우 효율적이기 때문에 덜 차단하는 것을 의미하는 것은 아닙니다.<br>
<img src="https://raw.githubusercontent.com/gorhill/uBlock/master/doc/benchmarks/privex-201502-16.png" /><br>
<sup>자세한 벤치마크는  
<a href="https://github.com/gorhill/uBlock/wiki/%C2%B5Block-and-others:-Blocking-ads,-trackers,-malwares">uBlock₀ 그리고 다른 프로그램: 광고 차단, 트래커, 멀웨어</a> 에서 확인이 가능합니다.
</p>

#### 빠른 테스트

- [인덱스](http://raymondhill.net/ublock/tests.html)
- [웹 페이지의 구성 요소](http://raymondhill.net/ublock/tiles1.html)
- [팝업](http://raymondhill.net/ublock/popup.html)

## 설치

부가 기능의 [필요한 권한](https://github.com/gorhill/uBlock/wiki/About-the-required-permissions)에 대해 읽어 주시기 바랍니다. 

#### 크로미움

직접 [수동](https://github.com/gorhill/uBlock/tree/master/dist#install)으로 최신 버전을 설치하거나, [크롬 웹 스토어](https://chrome.google.com/webstore/detail/ublock-origin/cjpalhdlnbpafiamejdnhcphjbkeiagm)에서 설치하실 수 있습니다. 오페라 브라우저를 사용하신다면, [오페라 스토어](https://addons.opera.com/en-gb/extensions/details/ublock/)에서 설치가  가능합니다.

대안으로, [chrisaljoudi/uBlock](https://github.com/chrisaljoudi/uBlock)을 [크롬 웹 스토어](https://chrome.google.com/webstore/detail/ublock/epcnnfbjfcgphgdmggkamkmgojdagdnn)에서 설치 할 수 있습니다. 전체 기능에서는 약간 다르지만, 같은 성능을 가지고 있습니다.

#### 파이어폭스

[파이어폭스 부가 기능 홈페이지](https://addons.mozilla.org/firefox/addon/ublock-origin/)에서 설치하거나, [uBlock0.firefox.xpi](https://github.com/gorhill/uBlock/releases) 파일을 다운로드 받아 최신 버전을 설치할 수 있습니다, 그리고 다운로드 받은 `xpi` 파일을 부가 기능 페이지에 드래그 하시면 됩니다.

대안으로, [chrisaljoudi/uBlock](https://github.com/chrisaljoudi/uBlock)을 [파이어폭스 부가 기능 홈페이지](https://addons.mozilla.org/firefox/addon/ublock/)에서 설치 할 수 있습니다. 전체 기능에서는 약간 다르지만, 같은 성능을 가지고 있으며, 구형 파이어폭스 기반 브라우저에 대해서도 적절히 지원하고 있습니다.

#### 사파리

uBlock Origin은 아직 사파리 브라우저를 지원하지 않습니다.

제일 좋은 방법은 [chrisaljoudi/uBlock](https://github.com/chrisaljoudi/uBlock)를 설치하는 것입니다. 이것은 공식적으로 사파리를 지원합니다.

#### 모든 브라우저에 대한 주의 사항

uBlock Origin의 높은 차단효율을 위해서는 동시에 다른 비효율적인 차단기를 사용하지 않는 것이 좋습니다. (예: 애드블록이나 애드블록 플러스) uBlock₀은 다른 인기있는 광고 차단기의 [그 이상입니다](#차단).

## 릴리즈 내역

[릴리즈 페이지](https://github.com/gorhill/uBlock/releases)에서 릴리즈 내역과 릴리즈에 대한 하이라이트 부분을 볼 수 있습니다.

## 정보

[uBlock Origin의 선언서](MANIFESTO.md).

무료이며, 오픈소스이며, 사용자를 위해 사용자가 만들었습니다. 어떠한 기부도 바라지 않습니다.

이 차단기에 포함되어 있는 필터가 없다면, 이 부가 기능은 쓸모가 없어집니다. 그러니 정말 어떤것이라도 기부하고 싶은 마음이 든다면, 당신이 사용중인 모두를 위해 무료로 쓸 수 있게 만들어진 필터 리스트를 위해 일하는 사람들을 생각해주세요.

[Crowdin](https://crowdin.net/project/ublock)에서 uBlock의 번역 작업을 도와줄 수 있습니다.

## 라이센스

[GPLv3](https://github.com/gorhill/uBlock/blob/master/LICENSE.txt).
