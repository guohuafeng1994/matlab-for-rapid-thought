clear;clc;
%读取该目录下的所有txt文件
%namelist ?= dir('E:\New\*.txt');
% 读取后namelist?的属性有
% name -- filename
% date -- modification date
% bytes -- number of bytes allocated to the file
% isdir -- 1 if name is a directory and 0 if not
targetNode=[56357,56651,56664,56666,56543,56671,56763,56751,56768,56565];
 datawrite=[];;%合并内容
 fn1='C:\Users\12291\Desktop\c.xlsx';%写入文件
%通过字符串拼接,获取绝对路径可以直接用[],也可以用strcat()函数
path = 'C:\Users\12291\Desktop\prec\';path,
namelist = dir([path,'*.txt']);
l = length(namelist);
P = cell(1,l);%定义一个细胞数组,用于存放所有txt文件
namelist(l).name;%这里获得的只是该路径下的文件名,如1.txt是相对路径
for i = 1:l
       filename{i} = [path,namelist(i).name];%通过字符串拼接获得的就是绝对路径了
       P=[];
    P = importdata(filename{i});
    index=[];
    for j=1:length(targetNode)
       temp= find(P(:,1)==targetNode(j));
       index=[index,temp];
    end
    datawrite=[datawrite;P(index,:)];
end
xlswrite(fn1,datawrite,'A')
% %存储的excel的位置和名称

