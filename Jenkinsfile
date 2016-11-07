node('docker') {
    def image = docker.image('hiono/texlive')
    image.pull()
    image.inside() {
        sh """
        pdflatex ogsde-man.tex
        makeindex ogsde-man.idx
        pdflatex ogsde-man.tex
        pdflatex ogsde-man.tex

        gs -sDEVICE=pdfwrite -dCompatibilityLevel=1.4 -dPDFSETTINGS=/prepress -dNOPAUSE -dQUIET -dBATCH -sOutputFile=DataExplorer-Manual.pdf ogsde-man.pdf
        """.stripIndent()
    }

    archiveArtifacts 'DataExplorer-Manual.pdf'
}
