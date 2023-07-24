# Projectsekai-wordle
Code for SEGA's otoge Projectsekai wordle  
2023/7/25  
这是pjsk开字符游戏的R代码,尽管我觉得并不会有多少人用R来玩wordle但还是发上来.  
如果要开始游戏,先运行climb.R以爬取歌曲名称,结果可能会因为网站更新有所调整.  
然后先运行game.R中的dictionary部分,在这里可以检查所有英文日文符号和变量名的对应关系,例如en_n对应的是英文n,jp_i对应的是日文平假片假和大小いイぃィ.  
然后设置n为要猜多少首歌,例如要猜10首的话请设置n=10.  
接下来请运行start_game()函数和game_process()函数,到这里就可以开始游戏了.  
依次运行代码  
game = start_game(n)  
  
game_song = game$game_song;game_song  
quiz = game$quiz;quiz  
quiz_song = game$quiz_song;quiz_song  
quiz_song_len = game$quiz_song_len;quiz_song_len  
  
as.matrix(quiz,ncol=1)  
在最后的输出里可以看到谜面，例如：  
 [1,] "8 ********"         
 [2,] "10 **********"      
 [3,] "3 ***"              
 [4,] "4 ****"             
 [5,] "14 **************"  
 [6,] "8 ********"       
 [7,] "2 **"             
 [8,] "1 *"              
 [9,] "2 **"             
[10,] "7 *******"        
然后请点击#first round里的代码,其中letter = yanyin代表第一个开出的字符是日语中的长音符.
as.matrix(game_process(clear_num = NULL, letter = letter , game_song = game_song , quiz_song = quiz_song , quiz_song_len = quiz_song_len),ncol=1)
as.matrix(game_song,ncol = 1)
在输出中可以看到第一轮的结果:
 [1,] "8 ********"       
 [2,] "10 **********"    
 [3,] "3 ***"            
 [4,] "4 ****"           
 [5,] "14 **************"
 [6,] "8 ***ー****"      
 [7,] "2 **"             
 [8,] "1 *"              
 [9,] "2 **"             
[10,] "7 *******"        
正确答案就在下方方便对照：
 [1,] "ボッカデラベリタ"
 [2,] "ontherocks"      
 [3,] "キティ"          
 [4,] "ヒビカセ"        
 [5,] "HappyHalloween"  
 [6,] "星空オーケストラ"
 [7,] "テオ"            
 [8,] "街"              
 [9,] "相生"            
[10,] "ONESELF"       
进入第二轮请运行#rounds中的代码,在letter = c(letter , chi)括号中第二个位置输入第二轮被开的字符,这里是平假名和片假名的chi(也可以一次性输入多个被开字符)
需要额外注意的是在as.matrix(game_process(clear_num = NULL, letter = letter , game_song = game_song , quiz_song = quiz_song , quiz_song_len = quiz_song_len),ncol=1)中,
如果没有被猜中的曲目需要把clear_num设置为NULL(clear_num = NULL),被猜中的歌曲序号请clear_num = c()括号中用逗号分隔开来.
已开字符:
ーちチ
谜面:
 [1,] "8 ********"       
 [2,] "10 **********"    
 [3,] "3 ***"            
 [4,] "4 ****"           
 [5,] "14 **************"
 [6,] "8 ***ー****"      
 [7,] "2 **"             
 [8,] "1 *"              
 [9,] "2 **"             
[10,] "7 *******"         
正确答案:
 [1,] "ボッカデラベリタ"
 [2,] "ontherocks"      
 [3,] "キティ"          
 [4,] "ヒビカセ"        
 [5,] "HappyHalloween"  
 [6,] "星空オーケストラ"
 [7,] "テオ"            
 [8,] "街"              
 [9,] "相生"            
[10,] "ONESELF"       
开o
letter = c(letter , o)

as.name(str_c(letter,collapse = ""))
as.matrix(game_process(clear_num = NULL, letter = letter , game_song = game_song , quiz_song = quiz_song , quiz_song_len = quiz_song_len),ncol=1)
as.matrix(game_song,ncol = 1)
已开字符:
ーちチoO
谜面:
 [1,] "8 ********"       
 [2,] "10 o*****o***"    
 [3,] "3 ***"            
 [4,] "4 ****"           
 [5,] "14 *********o****"
 [6,] "8 ***ー****"      
 [7,] "2 **"             
 [8,] "1 *"              
 [9,] "2 **"             
[10,] "7 O******"     
正确答案:
 [1,] "ボッカデラベリタ"
 [2,] "ontherocks"      
 [3,] "キティ"          
 [4,] "ヒビカセ"        
 [5,] "HappyHalloween"  
 [6,] "星空オーケストラ"
 [7,] "テオ"            
 [8,] "街"              
 [9,] "相生"            
[10,] "ONESELF"      
开te,且2已被猜出
letter = c(letter , te)

as.name(str_c(letter,collapse = ""))
as.matrix(game_process(clear_num = NULL, letter = letter , game_song = game_song , quiz_song = quiz_song , quiz_song_len = quiz_song_len),ncol=1)
as.matrix(game_song,ncol = 1)
已开字符:
ーちチoOてテ
谜面:
 [1,] "8 ********"       
 [2,] "10 ontherocks"    
 [3,] "3 *テ*"           
 [4,] "4 ****"           
 [5,] "14 *********o****"
 [6,] "8 ***ー****"      
 [7,] "2 テ*"            
 [8,] "1 *"              
 [9,] "2 **"             
[10,] "7 O******"    
正确答案:
 [1,] "ボッカデラベリタ"
 [2,] "ontherocks"      
 [3,] "キティ"          
 [4,] "ヒビカセ"        
 [5,] "HappyHalloween"  
 [6,] "星空オーケストラ"
 [7,] "テオ"            
 [8,] "街"              
 [9,] "相生"            
[10,] "ONESELF"       
重复运行直至所有歌名都开出.


目前已经发现的bug:
在letter = c(letter , )中不能添加letter = c(letter , "?")会导致谜面不能正常出现,部分歌名中含有?,如どんな結末がお望みだい？
