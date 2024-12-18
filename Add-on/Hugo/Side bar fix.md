Code works but the git node dependencies will not be overwritten , so over writing the file is a thing that can work.

A code to 
```html
{{ define "main" }}
  <div class="row flex-xl-nowrap">
    {{ if (in site.Params.doks.sectionNav .Section) -}}
    <div class="col-lg-5 col-xl-4 docs-sidebar{{ if ne site.Params.doks.navbarSticky true }} docs-sidebar-top{{ end }}{{ if site.Params.doks.headerBar }} docs-sidebar-offset{{ end }} d-none d-lg-block">
      <!-- Modified section menu partial -->
      {{ $currentSection := .Section }}
      {{ with .CurrentSection }}
        <nav class="docs-links" aria-label="Main navigation">
          <ul class="list-unstyled">
            {{ range where .Pages "Kind" "page" }}
              <li>
                <a href="{{ .RelPermalink }}" class="docs-link{{ if eq $.Page.RelPermalink .RelPermalink }} active{{ end }}">{{ .Title }}</a>
              </li>
            {{ end }}
            {{ range .Sections }}
              <li>
                <h3>{{ .Title }}</h3>
                <ul class="list-unstyled">
                  {{ range where .Pages "Kind" "page" }}
                    <li>
                      <a href="{{ .RelPermalink }}" class="docs-link{{ if eq $.Page.RelPermalink .RelPermalink }} active{{ end }}">{{ .Title }}</a>
                    </li>
                  {{ end }}
                </ul>
              </li>
            {{ end }}
          </ul>
        </nav>
      {{ end }}
    </div>
    {{ end -}}

    {{ if and (eq site.Params.doks.containerBreakpoint "fluid") (in .Site.Params.mainSections .Type) }}
      <div class="col container-fw d-lg-flex flex-lg-row justify-content-center mx-auto">
    {{ end }}

    {{ if ne .Params.toc false -}}
    <nav class="docs-toc{{ if ne site.Params.doks.navbarSticky true }} docs-toc-top{{ end }}{{ if site.Params.doks.headerBar }} docs-toc-offset{{ end }} d-none d-xl-block col-xl-3" aria-label="Secondary navigation">
      {{ partial "sidebar/docs-toc-desktop.html" . }}
    </nav>
    {{ end -}}

    {{ if .Params.toc -}}
    <main class="docs-content col-lg-11 col-xl-9">
    {{ else -}}
    <main class="docs-content col-lg-11 col-xl-9 mx-xl-auto">
    {{ end -}}
      {{ if site.Params.doks.breadcrumbTrail -}}
        <nav aria-label="breadcrumb">
          <ol class="breadcrumb">
            {{ partial "main/breadcrumb" . -}}
            <li class="breadcrumb-item active" aria-current="page">{{ .Title }}</li>
          </ol>
        </nav>
      {{ end }}

      <h1>{{ .Title }}</h1>
      
      {{ if ne .Params.toc false -}}
      <nav class="toc-mobile d-xl-none" aria-label="Quaternary navigation">
        {{ partial "sidebar/docs-toc-mobile.html" . }}
      </nav>
      {{ end -}}

      {{ if site.Params.doks.headlineHash -}}
        {{ partial "main/headline-hash" .Content }}
      {{ else -}}
        {{ .Content }}
      {{ end -}}

      <div class="page-footer-meta d-flex flex-column flex-md-row justify-content-between">
        {{ if site.Params.doks.lastMod -}}
          {{ partial "main/last-modified.html" . }}
        {{ end -}}
        {{ if site.Params.doks.editPage -}}
          {{ partial "main/edit-page.html" . }}
        {{ end -}}
      </div>

      {{ partial "main/docs-navigation.html" . }}
    </main>

    {{ if and (eq site.Params.doks.containerBreakpoint "fluid") (in .Site.Params.mainSections .Type) }}
      </div>
    {{ end }}
  </div>
{{ end }}
```

# Backup
```html
{{ define "main" }}
	<div class="row flex-xl-nowrap">
		{{ if (in site.Params.doks.sectionNav .Section) -}}
		<div class="col-lg-5 col-xl-4 docs-sidebar{{ if ne site.Params.doks.navbarSticky true }} docs-sidebar-top{{ end }}{{ if site.Params.doks.headerBar }} docs-sidebar-offset{{ end }} d-none d-lg-block">
			{{ partial "sidebar/section-menu.html" . }}
		</div>
		{{ end -}}
		{{ if and (eq site.Params.doks.containerBreakpoint "fluid") (in .Site.Params.mainSections .Type) }}
			<div class="col container-fw d-lg-flex flex-lg-row justify-content-center mx-auto">
		{{ end }}
		{{ if ne .Params.toc false -}}
		<nav class="docs-toc{{ if ne site.Params.doks.navbarSticky true }} docs-toc-top{{ end }}{{ if site.Params.doks.headerBar }} docs-toc-offset{{ end }} d-none d-xl-block col-xl-3" aria-label="Secondary navigation">
			{{ partial "sidebar/docs-toc-desktop.html" . }}
		</nav>
		{{ end -}}
		{{ if .Params.toc -}}
		<main class="docs-content col-lg-11 col-xl-9">
		{{ else -}}
		<main class="docs-content col-lg-11 col-xl-9 mx-xl-auto">
		{{ end -}}
			{{ if site.Params.doks.breadcrumbTrail -}}
				<!-- https://discourse.gohugo.io/t/breadcrumb-navigation-for-highly-nested-content/27359/6 -->
				<nav aria-label="breadcrumb">
					<ol class="breadcrumb">
						{{ partial "main/breadcrumb" . -}}
						<li class="breadcrumb-item active" aria-current="page">{{ .Title }}</li>
					</ol>
				</nav>
			{{ end }}
			<h1>{{ .Title }}</h1>
			<!-- <p class="lead">{{ .Params.lead | safeHTML }}</p> -->
			{{ if ne .Params.toc false -}}
			<nav class="toc-mobile d-xl-none" aria-label="Quaternary navigation">
				{{ partial "sidebar/docs-toc-mobile.html" . }}
			</nav>
			{{ end -}}

			{{ if site.Params.doks.headlineHash -}}
				{{ partial "main/headline-hash" .Content }}
			{{ else -}}
				{{ .Content }}
			{{ end -}}
			<div class="page-footer-meta d-flex flex-column flex-md-row justify-content-between">
				{{ if site.Params.doks.lastMod -}}
					{{ partial "main/last-modified.html" . }}
				{{ end -}}
				{{ if site.Params.doks.editPage -}}
					{{ partial "main/edit-page.html" . }}
				{{ end -}}
			</div>
			{{ partial "main/docs-navigation.html" . }}
			<!--
			{{ if not .Site.Params.options.collapsibleSidebar -}}
				{{ partial "main/docs-navigation.html" . }}
			{{ else -}}
				<div class="my-n3"></div>
			{{ end -}}
			-->
		</main>
		{{ if and (eq site.Params.doks.containerBreakpoint "fluid") (in .Site.Params.mainSections .Type) }}
			</div>
		{{ end }}
	</div>
{{ end }}

```