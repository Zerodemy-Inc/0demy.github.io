--- 
title: "All Books Under Books Directory"
---
<ul>
        {{ $genres := slice }}
        {{ range .Site.RegularPages }}
            {{ $currentGenres := .Params.genre }}
            {{ range $currentGenres }}
                {{ $genres = $genres | append . }}
            {{ end }}
        {{ end }}
        {{ $uniqueGenres := slice }}
        {{ range $genres }}
            {{ if not (in . $uniqueGenres) }}
                {{ $uniqueGenres = $uniqueGenres | append . }}
            {{ end }}
        {{ end }}
        {{ range $uniqueGenres }}
            <li>{{ . }}</li>
        {{ end }}
    </ul>