# left-join
joining stewardship and street tree data so that tree stewardship has spatial locations

-- look at tree ID for stewardship data, needs to be same type as tree ID for street tree tree ID

select "row.names", id, "dateDone", "durationInMinutes", "activitiesDone", groups, "treeId"::text as treeID_txt from env_assets.dpr_stewardship_20180629;

select zipcode, boroname, tree_dbh, geom_2263, tree_id from env_assets.streettrees2015;


-- LEFT JOIN
-- left join of stewardship data with street tree geometries
-- make sure treeIDs are cast as same type

--create table env_assets.stewardship_streettrees_join AS
select dpr_stewardship_20180629."row.names", dpr_stewardship_20180629.id, dpr_stewardship_20180629."dateDone", dpr_stewardship_20180629."durationInMinutes", dpr_stewardship_20180629."activitiesDone", dpr_stewardship_20180629.groups, dpr_stewardship_20180629."treeId", streettrees2015.geom_2263 from env_assets.dpr_stewardship_20180629 
left join env_assets.streettrees2015 
on dpr_stewardship_20180629."treeId"::text = streettrees2015.tree_id;
