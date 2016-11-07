node('docker') {
    checkout scm

    def image = docker.image('hiono/texlive')
    image.pull()
    image.inside() {
        sh """
        pdflatex -interaction=nonstopmode ogsde-man.tex
        makeindex ogsde-man.idx
        pdflatex -interaction=nonstopmode ogsde-man.tex
        pdflatex -interaction=nonstopmode ogsde-man.tex

        gs -sDEVICE=pdfwrite -dCompatibilityLevel=1.4 -dPDFSETTINGS=/prepress -dNOPAUSE -dQUIET -dBATCH -sOutputFile=DataExplorer-Manual.pdf ogsde-man.pdf
        """.stripIndent()
    }

    archiveArtifacts 'DataExplorer-Manual.pdf'
}
