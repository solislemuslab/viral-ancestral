## Flaviridae

### joint sequence

raxml-ng –msa flaviviridae\_w\_outgroup\_wo\_flavivirus\_aligned.fasta
–model GTR+G –prefix flaviviridae\_tree –threads 2 –seed 2

    rm(list=ls())
    library(ape)
    library(phylotools)
    library(phytools)

    ## Loading required package: maps

    library(phangorn)
    library(geiger)
    data=read.fasta("./flaviviridae/flaviviridae_w_outgroup_wo_flavivirus_aligned.fasta")

    # Unroot tree
    tree.1=read.tree("./flaviviridae/flaviviridae_tree.raxml.bestTree")
    plot(tree.1)

![](new_ds_files/figure-markdown_strict/unnamed-chunk-1-1.png)

    tree.1_unroot=unroot(tree.1)
    plot(tree.1_unroot, type="unrooted",edge.width=2, no.margin=TRUE)

![](new_ds_files/figure-markdown_strict/unnamed-chunk-1-2.png)

    # Root at outgroup
    tree.2=root(tree.1_unroot,outgroup="M96751.1.1-388_Bovine_viral_diarrhea_virus_1-SD1_polyprotein_gene_complete_cds")
    index=which(tree.2[["tip.label"]]=="M96751.1.1-388_Bovine_viral_diarrhea_virus_1-SD1_polyprotein_gene_complete_cds")

    # Romove outgroup
    name_without_outgroup=tree.2[["tip.label"]][-(index)]
    tree.3=keep.tip(tree.2,name_without_outgroup)
    plot(tree.3)

![](new_ds_files/figure-markdown_strict/unnamed-chunk-1-3.png)

    #write.tree(tree.3,"./flaviviridae/flaviviridae_wo_outgroup_wo_flavivirus_w_root.tree")

    # Remove the name in the ancestral sequences
    index2=which(data$seq.name=="M96751.1.1-388_Bovine_viral_diarrhea_virus_1-SD1_polyprotein_gene_complete_cds")
    seq_deletion=data[-(index2),]
    #dat2fasta(seq_deletion,"./flaviviridae/flaviviridae_wo_outgroup_wo_flavivirus_aligned.fasta")

### estimate ancestral sequence

raxml-ng –ancestral –msa
flaviviridae\_wo\_outgroup\_wo\_flavivirus\_aligned.fasta –tree
flaviviridae\_wo\_outgroup\_wo\_flavivirus\_w\_root.tree –model GTR+G
–prefix flaviviridae\_ancestral

### plot the ancestral tree with node labels

    tree=read.tree("./raxml_result/ancestor/flaviviridae_ancestral.raxml.ancestralTree")
    plot(tree, show.node.label = T)

![](new_ds_files/figure-markdown_strict/unnamed-chunk-2-1.png)

## Picornaviridae

### joint sequence

raxml-ng –msa picornaviridae\_w\_outgroup\_aligned.fasta –model GTR+G
–prefix picornaviridae\_tree –threads 2 –seed 2

    data=read.fasta("./picornaviridae/picornaviridae_w_outgroup_aligned.fasta")

    # Unroot tree
    tree.1=read.tree("./picornaviridae/picornaviridae_tree.raxml.bestTree")
    plot(tree.1)

![](new_ds_files/figure-markdown_strict/unnamed-chunk-3-1.png)

    # outgroup:"NC_039209.1-1-921_Equine_rhinitis_A_virus_strain_PERV-1_complete_genome"
    tree.1_unroot=unroot(tree.1)
    plot(tree.1_unroot, type="unrooted",edge.width=2, no.margin=TRUE)

![](new_ds_files/figure-markdown_strict/unnamed-chunk-3-2.png)

    # Root at outgroup
    tree.2=root(tree.1_unroot,outgroup="NC_039209.1-1-921_Equine_rhinitis_A_virus_strain_PERV-1_complete_genome")
    index=which(tree.2[["tip.label"]]=="NC_039209.1-1-921_Equine_rhinitis_A_virus_strain_PERV-1_complete_genome")

    # Remove outgroup and root the tree
    name_without_outgroup=tree.2[["tip.label"]][-(index)]
    tree.3=keep.tip(tree.2,name_without_outgroup)
    plot(tree.3)

![](new_ds_files/figure-markdown_strict/unnamed-chunk-3-3.png)

    #write.tree(tree.3,"./picornaviridae/picornaviridae_wo_outgroup_wo_picornavirus_w_root.tree")

    # Remove the name in the ancestral sequences
    index2=which(data$seq.name=="NC_039209.1-1-921_Equine_rhinitis_A_virus_strain_PERV-1_complete_genome")
    seq_deletion=data[-(index2),]
    #dat2fasta(seq_deletion,"./picornaviridae/picornaviridae_wo_outgroup_wo_picornavirus_aligned.fasta")

### estimate ancestral sequence

raxml-ng –ancestral –msa
picornaviridae\_wo\_outgroup\_wo\_picornavirus\_aligned.fasta –tree
picornaviridae\_wo\_outgroup\_wo\_picornavirus\_w\_root.tree –model
GTR+G –prefix picornaviridae\_ancestral

### plot the ancestral tree

    tree=read.tree("./raxml_result/ancestor/picornaviridae_ancestral.raxml.ancestralTree")
    plot(tree, show.node.label = T)

![](new_ds_files/figure-markdown_strict/unnamed-chunk-4-1.png)

## Picornaviridae

### joint sequence

raxml-ng –msa potyviridae\_poacevirus\_w\_outgroup\_aligned.fasta –model
GTR+G –prefix potyviridae\_tree –threads 2 –seed 2

    data=read.fasta("./potyviridae/potyviridae_poacevirus_w_outgroup_aligned.fasta")

    # Unroot tree
    tree.1=read.tree("./potyviridae/potyviridae_tree.raxml.bestTree")
    plot(tree.1)

![](new_ds_files/figure-markdown_strict/unnamed-chunk-5-1.png)

    tree.1_unroot=unroot(tree.1)
    plot(tree.1_unroot, type="unrooted",edge.width=2, no.margin=TRUE)

![](new_ds_files/figure-markdown_strict/unnamed-chunk-5-2.png)

    # Root at outgroup
    # There are two outgroups here and I only root at one of it:"NC_018572.1-1-369_Caladenia_virus_A_complete_genome"
    tree.2=root(tree.1_unroot,outgroup="NC_018572.1-1-369_Caladenia_virus_A_complete_genome")
    index=which(tree.2[["tip.label"]]=="NC_018572.1-1-369_Caladenia_virus_A_complete_genome")

    # Remove outgroup
    name_without_outgroup=tree.2[["tip.label"]][-(index)]
    tree.3=keep.tip(tree.2,name_without_outgroup)
    plot(tree.3)

![](new_ds_files/figure-markdown_strict/unnamed-chunk-5-3.png)

    #write.tree(tree.3,"./potyviridae/potyviridae_wo_outgroup_wo_potyvirus_w_root.tree")

    # Remove the name in the ancestral sequences
    index2=which(data$seq.name=="NC_018572.1-1-369_Caladenia_virus_A_complete_genome")
    seq_deletion=data[-(index2),]
    #dat2fasta(seq_deletion,"./potyviridae/potyviridae_wo_outgroup_wo_potyvirus_aligned.fasta")

### estimate ancestral sequence (less than four sequence)

raxml-ng –ancestral –msa
potyviridae\_wo\_outgroup\_wo\_potyvirus\_aligned.fasta –tree
potyviridae\_wo\_outgroup\_wo\_potyvirus\_w\_root.tree –model GTR+G
–prefix potyviridae\_ancestral

### plot the ancestral tree

    tree=read.tree("./raxml_result/ancestor/potyviridae_ancestral.raxml.ancestralTree")
    plot(tree, show.node.label = T)

![](new_ds_files/figure-markdown_strict/unnamed-chunk-6-1.png)
