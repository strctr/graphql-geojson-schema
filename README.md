# GraphQL GeoJson Schema 

GraphQL schema types for GeoJson primitives.

```graphql
# #################################
# ######## GeoJSON Types ##########
# #################################

"""
Represents pair of coordinates that are part of a GeoJSON structure in a format [number, number]
https://tools.ietf.org/html/rfc7946#section-3.1.1
"""
scalar GeoJsonPosition

"""
Point geometry object.
https://tools.ietf.org/html/rfc7946#section-3.1.2
"""
type GeoJsonPoint {
  "Contains value \"Point\""
  type: String!
  
  "Point coordinates in format [number, number]"
  coordinates: GeoJsonPosition!
}

"""
Multi-Point geometry object.
https://tools.ietf.org/html/rfc7946#section-3.1.3
"""
type GeoJsonMultiPoint {
  "Contains value \"MultiPoint\""
  type: String!
  
  "Multi-Point coordinates in format [[number, number]...]"
  coordinates: [GeoJsonPosition!]!
}

"""
LineString geometry object.
https://tools.ietf.org/html/rfc7946#section-3.1.4
"""
type GeoJsonLineString {
  "Contains value \"LineString\""
  type: String!
  
  "LineString coordinates in format [[number, number]...]"
  coordinates: [GeoJsonPosition!]!
}

"""
MultiLineString geometry object.
https://tools.ietf.org/html/rfc7946#section-3.1.5
"""
type GeoJsonMultiLineString {
  "Contains value \"MultiLineString\""
  type: String!
  
  "MultiLineString coordinates in format [[[number, number]...]...]"
  coordinates: [[GeoJsonPosition!]!]!
}

"""
Polygon geometry object.
https://tools.ietf.org/html/rfc7946#section-3.1.6
"""
type GeoJsonPolygon {
  "Contains value \"Polygon\""
  type: String!
  
  "Polygon coordinates in format [[[number, number]...]...]"
  coordinates: [[GeoJsonPosition!]!]!
}

"""
MultiPolygon geometry object.
https://tools.ietf.org/html/rfc7946#section-3.1.7
"""
type GeoJsonMultiPolygon {
  "Contains value \"MultiPolygon\""
  type: String!
  
  "MultiPolygon coordinates in format [[[[number, number]...]...]...]"
  coordinates: [[[GeoJsonPosition!]!]!]!
}

"""
Geometry Collection
https://tools.ietf.org/html/rfc7946#section-3.1.8
"""
type GeoJsonGeometryCollection {
  "Contains value \"GeometryCollection\""
  type: String!
  
  "Array of geometries"
  geometries: [GeoJsonGeometry!]!
}

"""
Geometry object.
https://tools.ietf.org/html/rfc7946#section-3
"""
union GeoJsonGeometry =
    GeoJsonPoint
  | GeoJsonMultiPoint
  | GeoJsonLineString
  | GeoJsonMultiLineString
  | GeoJsonPolygon
  | GeoJsonMultiPolygon
  | GeoJsonGeometryCollection

"""
A feature object which contains a geometry and associated properties.
https://tools.ietf.org/html/rfc7946#section-3.2
"""
type GeoJsonFeature {
  "Contains value \"Feature\""
  type: String!
  
  "The feature's geometry"
  geometry: GeoJsonGeometry!
}

"""
A collection of feature objects.
https://tools.ietf.org/html/rfc7946#section-3.3
"""
type GeoJsonFeatureCollection {
  "Contains value \"FeatureCollection\""
  type: String!
  
  "Array of features"
  features: [GeoJsonFeature]!
}

"""
Union of GeoJSON objects.
"""
union GeoJSON = GeoJsonGeometry | GeoJsonFeature | GeoJsonFeatureCollection
```
