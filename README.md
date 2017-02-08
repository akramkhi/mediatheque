# mediatheque

##Pour l'identification de coté Administrateur :
il suffit de se connecter avec
                           email : media@gmail.com
                           md-pass: media

Pour la table de client y'a un champ " mode" : true pour un administrateur et false pour client

///

create table "AKRAM".CLIENT
(
	ID_CLIENT INTEGER  not null   GENERATED ALWAYS AS IDENTITY (START WITH 1,INCREMENT BY 1) primary key,
	NOM_CLIENT VARCHAR(25) not null,
	PRENOM_CLIENT VARCHAR(25) not null,
	ADRESSE_CLIENT VARCHAR(50) not null,
	MODE BOOLEAN default false not null,
	EMAIL VARCHAR(25) default '" "' not null,
	MD_PASS VARCHAR(10) default ' ' not null
);

create table "AKRAM".TYPE
(
	ID_TYPE VARCHAR(10) not null primary key,
	LIBELLE_TYPE VARCHAR(25) not null
);
create table "AKRAM".PRODUIT
(
	ID_PRODUIT VARCHAR(10) not null primary key,
	LIBELLE_PRODUIT VARCHAR(25) not null,
	ID_TYPE VARCHAR(10) not null
);

create table "AKRAM".PRETER
(
	ID_CLIENT INTEGER  not null ,
	ID_PRODUIT VARCHAR(10) not null,
	DATE_PR DATE not null,
	DATE_RETOUR DATE not null,
	primary key (ID_CLIENT, ID_PRODUIT)
);


create table "AKRAM".MESSAGE
(
	ID INTEGER GENERATED ALWAYS AS IDENTITY (START WITH 1, INCREMENT BY 1) not null primary key,
	EMAIL VARCHAR(30) not null,
	NOM VARCHAR(25) not null,
	PRENOM VARCHAR(25) not null,
	DATE DATE not null,
	SUJET VARCHAR(40) not null,
	MESSAGE VARCHAR(125) not null
);

ALTER TABLE produit ADD CONSTRAINT pr_FK
Foreign Key (id_type) REFERENCES type (id_type);

ALTER TABLE preter ADD CONSTRAINT pclient_FK
Foreign Key (id_client) REFERENCES client (id_client);

ALTER TABLE preter ADD CONSTRAINT pproduit_FK
Foreign Key (id_produit) REFERENCES produit (id_produit);

insert into client (nom_client,prenom_client,adresse_client,mode,email,md_pass)
values ('khi','akram','France',true,'media@gmail.com','media');


insert into type (id_type,libelle_type) values ('cd','CD');
insert into type(id_type,libelle_type) values ('dvd','DVD');
insert into type(id_type,libelle_type) values ('livre','LIVRE');

insert into produit (id_produit,libelle_produit,id_type) values ('1','NodeJS','cd');
