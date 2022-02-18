# Transposons
#TEdenovo using REPET v2
#==============================================================================

#TEdenovo.py from REPET v2 WORKS with phyton2:

#module load python/2.7.15

#You can run TEdenovo using the sequence provided as example "DmelChr4.fa", or replace with your fasta file (assembly) of interest.

#RENAME the project name in the configuration file TEdenovo.cfg
#[project]
#project_name: DmelChr4

#Edit TEdenovo.cfg and ./run in order to adapt it to your personal situation. More in https://urgi.versailles.inra.fr/Tools/REPET/TEdenovo-tuto

#The output is a MCL-filtered library of TEs located in {NAME}_Blaster_GrpRecPil_Struct_Map_TEclassif_Filtered_MCL

#==============================================================================

On the FASTA files you use:
	* There is a 15-character limit on the name of the file (and the project name)
	* Make sure there is a line break at least once every 60 bases
	* Make sure there are no illegal characters in the FASTA headers

##LINE BREAK (https://bioinf.shenwei.me/seqkit/)
seqkit seq -w 60 Sp.fasta > Sp.fna

##RENAME fasta headers
awk '/^>/{print ">Sp_ctg" ++i; next}{print}' < Sp.fna > Sp.fst

##ALL CAPITAL LETTERS
awk 'BEGIN{FS=" "}{if(!/>/){print toupper($0)}else{print $1}}' Sp.fst > Sp.fa

#==============================================================================
