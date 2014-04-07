healtheq
========
use seba;

create table if not exists balance (
 NewMemberID bigint,
 CachedBalance double
)
row format delimited fields terminated by ',';
LOAD DATA INPATH '/user/seba/data/health_equity/Balance.csv' OVERWRITE INTO TABLE balance;

create table if not exists member (
 NewMemberID bigint,
 State string,
 Zip string,
 Gender string,
 BirthYear bigint,
 HsaEffectiveDate string	
)row format delimited fields terminated by ',';
LOAD DATA INPATH '/user/seba/data/health_equity/Member.csv' OVERWRITE INTO TABLE member;

create table if not exists claim_detail (
﻿ NewClaimID bigint,
 CPTCode string
)row format delimited fields terminated by ',';

LOAD DATA INPATH '/user/seba/data/health_equity/ClaimDetail.csv' OVERWRITE INTO TABLE claim_detail;

create table if not exists claim ( 
﻿ NewClaimID bigint,
 NewMemberID bigint,
 DependentServiced string,
 ClaimType string,
 DateReceived string,
 DateProcessed string,
 ServiceStart string,
 ServiceEnd string,
 RepricedAmount double,
 PatientResponsibilityAmount double
)
row format delimited fields terminated by ',';
LOAD DATA INPATH '/user/seba/data/health_equity/Claim.csv' OVERWRITE INTO TABLE claim;



create table if not exists contribution_and_payment (
 ﻿NewMemberID bigint,
 Amount double,
 Category string,
 PaymentAvailableDate string
) row format delimited fields terminated by ',';
LOAD DATA INPATH '/user/seba/data/health_equity/ClaimDetail.csv' OVERWRITE INTO TABLE contribution_and_payment;

create table if not exists dependent(
 ﻿NewMemberID bigint,
 DependentID bigint,
 Relationship string,
 BirthYear bigint,
 Gender string,
 State string,
 Zip string
) row format  delimited fields terminated by ',';
LOAD DATA INPATH '/user/seba/data/health_equity/Dependent.csv' OVERWRITE INTO TABLE dependent;
healtheq
