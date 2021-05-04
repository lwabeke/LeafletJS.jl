# LeafletJS

[![Build Status](https://travis-ci.org/yeesian/LeafletJS.jl.svg?branch=master)](https://travis-ci.org/yeesian/LeafletJS.jl)

[![Coverage Status](https://coveralls.io/repos/yeesian/LeafletJS.jl/badge.svg?branch=master&service=github)](https://coveralls.io/github/yeesian/LeafletJS.jl?branch=master)

[![codecov.io](http://codecov.io/github/yeesian/LeafletJS.jl/coverage.svg?branch=master)](http://codecov.io/github/yeesian/LeafletJS.jl?branch=master)

```julia
LeafletMap([
        Layer(df, geomcol, color=..., size=...),
        Layer(df, geomcol, )
    ],
    [center]
)
```

Example based on usage in
https://nbviewer.jupyter.org/github/yeesian/LeafletExamples.jl/blob/master/notebook/leaflet-providers.ipynb

This works in IJulia notebooks

```julia
using LeafletJS, GeoJSON
;wget https://raw.githubusercontent.com/awoodruff/leaflet-intro/gh-pages/neighborhoods.geojson
;wget https://raw.githubusercontent.com/awoodruff/leaflet-intro/gh-pages/rodents.geojson

layers = Vector{Layer}(undef,0)
nbhd = GeoJSON.parsefile("neighborhoods.geojson")
rodents = GeoJSON.parsefile("rodents.geojson");
push!(layers, Layer(nbhd))
push!(layers, Layer(rodents))

LeafletMap(layers, [42.35, -71.08])

LeafletMap(layers, [42.35, -71.08], provider=Provider.Esri(:World_Imagery))

