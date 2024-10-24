# geopandas-notes

invalid_geometries = banana_splits.is_empty]
print(invalid_geometries)

invalid_geometries = banana_splits.is_vaalid]
print(invalid_geometries)

from shapely.geometry import Polygon

def check_collinearity(geom):
    if geom.geom_type == 'Polygon':
        coords = list(geom.exterior.coords)
        return len(set(coords)) < 3  # Less than 3 unique points means collinear or insufficient points
    return False

banana_splits['is_collinear'] = banana_splits.geometry.apply(check_collinearity)
collinear_geometries = buffer_time_dict[b][key][buffer_time_dict[b][key]['is_collinear']]
print(collinear_geometries)

def check_closed(geom):
    if geom.geom_type == 'Polygon':
        exterior = geom.exterior
        return exterior.coords[0] == exterior.coords[-1]
    return True  # Non-polygon geometries are considered closed for this check


banana_splits['is_closed'] = banana_splits.geometry.apply(check_closed)
non_closed_geometries = banana_splits[~banana_splits['is_closed']]
print(non_closed_geometries)
