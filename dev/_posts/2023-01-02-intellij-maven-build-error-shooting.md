---


title:  "[spring] 어플리케이션 발행하기"
date: 2023-01-02 11:32:00 +0900
last_modified_at: 2023-01-02 11:32:00 +0900
header:
  teaser: /assets/images/unsplash/github-842ofHC6MaI.jpg
  overlay_image: /assets/images/unsplash/github-842ofHC6MaI.jpg
  overlay_filter: 0.5
  caption: "Photo credit: [**Unsplash**](https://unsplash.com/photos/842ofHC6MaI)"

toc: true
toc_sticky: true

tags:
  - spring
  - maven
---

invalid item 'org.eclipse.m2e.MAVEN2_CLASSPATH_CONTAINER' in the dependencies list

Eclipse/ Intellij 최초 프로젝트 메이븐 빌드 시 위와 같은 오류가 확인된다면   
[홈]/.project [홈]/.classpath 의 설정 문제이므로, 아래와 같이 설정 추가로 조치 하면 된다.

## Cause

- Eclipse/ Intellij 에서 사용하는 메이븐 플러그인은 
- Sonatype 에서 만든 m2eclipse 플러그인과 
- 이클립스 공식 플러그인으로 합쳐진 m2e 플러그인이 있다.
- git으로 외부 프로젝트를 받을 경우 위 두 플러그인을 모두 추가해야 오류를 피해갈 수 있다.

## Solution

[홈]/.project 
아래 두 설정을 추가  

```
<buildSpec>
 ...
  <buildCommand>
    <name>org.maven.ide.eclipse.maven2Builder</name>
    <arguments>
    </arguments>
  </buildCommand>
  <buildCommand>
    <name>org.eclipse.m2e.core.maven2Builder</name>
    <arguments>
    </arguments>
  </buildCommand>
  ...
</buildSpec>
```
```
<natures>
  ...
  <nature>org.maven.ide.eclipse.maven2Nature</nature>
  <nature>org.eclipse.m2e.core.maven2Nature</nature>
  ...
</natures> 
```

[홈]/.classpath 
아래 설정 추가   

```
<classpath>
  ...
  <classpathentry kind="con" path="org.maven.ide.eclipse.MAVEN2_CLASSPATH_CONTAINER"/>
  <classpathentry kind="con" path="org.eclipse.m2e.MAVEN2_CLASSPATH_CONTAINER"/>
  ...
</classpath>
```

