### MODELS : exercice de groupe

### mes_App

* Blog
* Menu
* About
* configuration
* Reservation
* Contact
* Horraire


### Mes_models

# blog_model
```python
#--------------------import--blog-----------#
from django.db import models
from django.contrib.auth.models import User
# Create your models here.
#------------------------ blog_app_model --------------#
class Timemodels(models.Model):
    date_add =  models.DateTimeField(auto_now_add=True)
    date_update =  models.DateTimeField(auto_now=True)
    
    
class Tag(Timemodels):
    nom = models.CharField(max_length=225)

class Categorie(Timemodels):
    titre =  models.CharField(max_length=255)
    description =  models.TextField()
    status =  models.BooleanField(default=True)
    image = models.ImageField(upload_to='categorie', blank=True)
    nom =  models.ForeignKey(User,on_delete=models.CASCADE)
    
    
    
class Article(Timemodels):
    titre =  models.CharField(max_length=255)
    categorie_id =  models.ForeignKey(Categorie,on_delete=models.CASCADE, related_name="categorie")
    description =  models.TextField()
    status =  models.BooleanField(default=True)
    photo = models.ImageField(upload_to ='article', blank=True)
    tag_name = models.ManyToManyField(Tag)
    nom =  models.ForeignKey(User,on_delete=models.CASCADE)
    
    
class Commentaire(Timemodels):
    article_id =  models.ForeignKey(Article,on_delete=models.CASCADE, related_name="article_poster")
    nom = models.CharField(max_length=255)
    email = models.EmailField()
    website = models.URLField(max_length=250)
    contenu =  models.TextField()
    status =  models.BooleanField(default=True)
    
class Reply(Timemodels):
    nom = models.CharField(max_length=255)
    email = models.EmailField()
    website = models.URLField(max_length=250)
    comment = models.ForeignKey(Commentaire,on_delete=models.CASCADE, related_name="reponse")
    contenu =  models.TextField()
    
class replytwo(Timemodels):
    nom = models.CharField(max_length=255)
    email = models.EmailField()
    website = models.URLField(max_length=250)
    contenu =  models.TextField()
    reponse = models.ForeignKey(Reply,on_delete=models.CASCADE, related_name="reply")
    
```  
# Menu_model
```python
#---------------Menu------app-----#


class Timemodels(models.Model):
    date_add =  models.DateTimeField(auto_now_add=True)
    date_update =  models.DateTimeField(auto_now=True)
    
class MCategorie(Timemodels):
    nom = models.CharField(max_length=255)
    
class Recette(Timemodels):
    categorie = models.ForeignKey(MCategorie,on_delete=models.CASCADE, related_name="cate")
    nom = models.CharField(max_length=255)
    price = models.FloatField()
    ingrediens =  models.TextField()
    image = models.ImageField(upload_to='image',)

 
class Panier(models.Model):
    user_id =  models.ForeignKey(User,on_delete=models.CASCADE, related_name="user")
    recette = models.ManyToMany(recette)
    date_add = models.DateTimeField(auto_now_add=True)
    regler = models.BooleanField(default=False)
   
class Commande(models.Model):
    panier_id = models.ForeignKey(Panier,on_delete=models.CASCADE, related_name="panier_id")
    mode_payement = models.CharField(choices=PAYEMENT_CHOICES, max_length=2)
    country = CountryField(multiple=False)
    date_add =  models.DateTimeField(auto_now_add=True)
    
```   

# Services_app(about)
```python

#-------service-----#
class Personel (Timemodels):
    nom = models.CharField(max_length=250)
    image = models.ImageField(upload_to='image')
    fonction = models.CharField(max_length=250)
    facebook =  models.URLField(max_length=250)
    instagrame =  models.URLField(max_length=250)
    twitter =  models.URLField(max_length=250)
    googleplus =  models.URLField(max_length=250)
    
class TypeService(Timemodels):
    icon =models.CharField(max_length=250)
    titre = models.CharField(max_length=250)
    descriptions = models.TextField() 
    
class Appreciation(Timemodels):
    image = models.ImageField(upload_to='image')
    nom = models.CharField(max_length=255)
    fonction = models.CharField(max_length=255)
    description = models.TextField()
    
``` 
# Reservation..
```python

#----------------reservation-----------#
class reservation(Timemodels):
    phone = models.IntegerField()
    nom = models.CharField(max_length=255)
    email = models.EmailField()
    date = models.CharField()
    time = models.TimeField()
    person = models.IntegerField()

``` 
# Horaire..
```python

#----------------Horaire-----------#

class Horaire(Timemodels):
    jour = models.CharField(max_length=255)
    ouverture = models.TimeField()
    fermeture = models.TimeField()

``` 

# Contact
```python

#--------------Contact-----------#

class Contact(Timemodels):

    nom = models.CharField(max_length=255)
    email = models.EmailField()
    subject = models.CharField(max_length=255)
    message =  models.TextField()
  
``` 

# Newsller
```python

#--------------Newsller-----------#

class newsller(Timemodels):
    email = models.EmailField()

``` 


# config
```python

#--------------CONfIG-----------#

class info(Timemodels):
    numero = models.CharField(max_length=255)
    email = models.EmailField()
    website = models.URLField(max_length=250)
    addresse = models.CharField(max_length=255)
    facebook =  models.URLField(max_length=250)
    instagrame =  models.URLField(max_length=250)
    twitter =  models.URLField(max_length=250)
    googleplus =  models.URLField(max_length=250)
    description_gauche_footer =  models.CharField(max_length=255)
    description_droite_footer =  models.CharField(max_length=255)
    
 
#---------------------et ici nous aurons une class pour chaque page c'est-a_dire-------#
#exemple pour la page about 
class about(models.Model):
     nom = models.CharField(max_length=255)
     background_image =models.ImageField(upload_to='about')
      etc... pour chaque element qui doit venir de la bd 



``` 

# FIN...


    
    


