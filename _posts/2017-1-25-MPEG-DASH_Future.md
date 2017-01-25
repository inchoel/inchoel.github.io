---
layout: post
title: MPEG-DASH 그리고 앞으로 발전방향은
---

## MPEG-DASH
MPEG DASH는 HTTP를 통해서 분할된 미디어 컨텐츠를 스트리밍하기에 좋은 포멧을 제공한다. DASH client들은 유효한 대역폭과 로컬자원들에 기반하여 미디어 데이터 요청을 하는 client-pull 패러다임을 따른다. 이러한 방식은 CDN 인프라환경에서 server-push 기술들보다 더 쉽게 전개할 수 있음이 증명되어 졌다. 그러나 프리미엄 사용자들에 대해서 지속적이고 높은 품질의 서비스를 제공하기에 한계에 부딪혔다. MPEG은 이 이슈를 MPEG DASH part 5. Server and Network-assisted DASH(SAND)를 통해서 다루고 있다. SAND의 중요한 특징은 품질관련 보조정보를 위한 비동기적인 network-to-client 그리고 network-to-network 통신이다.

## SAND
미디어 스트리밍 기술들은 과거 몇년 동안 진화를 거듭해왔다. HTTP기반의 adaptive streaming은 오늘날 인터넷을 통한 스트리밍의 최선의 선택이라 할 수 있다. 많은 표준 및 업계 (DVB, 3GPP, HbbTV, DASH-IF)에서 DASH를 채택했다. DASH는 client-pull 기반으로 사용되어지도록 설계되었다. DASH client는 manifest file(MPD)를 받아서 메타데이터에 기반한 컨텐츠 세그먼트를 선택하고 다운받으며, 렌더링 한다.
그러나 DASH의 기본적인 decentralized 그리고 client-driven 특성은 몇가지 단점을 가지고 있다. Service provider가 client의 동작을 제어하기 어렵다는 것이 그중 하나라고 할 수 있다. 결과적으로 지속적인 고품질의 서비스를 제공하는 것을 어렵게 하기도 한다. 이처럼 품질에 영향을 주는 상황에 대한 많은 사례가 있다. 네트워크 실패 혹은 재설정, 접근오류로 인한 결과들로 MPD에 언급된 자원들은 더 이상 유효하지 않게 될 수 있다. hand-over 혹은 cache miss 등이 대역폭 감소로 해석될 때, DASH client는 낮은 품질의 세그먼트로 잘못 전환 할 수 있다. 대량의 live DASH 스트리밍은 CDN내의 많은 cache miss를 유발한다. DASH client는 불필요하게 낮은 품질의 세그먼트를 시작하고 대역폭 정보를 획득한 이후에 높은 품질 세그먼트를 가져올 수 있다. 공유된 대역폭에 대해서 두개 이상의 DASH client들은 경쟁을 하며, 이로 인해서 불필요한 행동을 하거나 출렁거림을 발생시킨다. 결과적으로 service provider는 premium quality를 보장할 수 없다.
MPEG은 이러한 사례를 수집하고 해결책을 강구했고 2015년 2월에 MPEG DASH part 5 SAND를 시작했다. 여기서는 이슈들은 해결하기 위한 architecture, data model, protocol 을 정의했다.
